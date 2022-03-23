**Proposal Due Date**
August 2022

**Proposal Overview**

Implementation of oracles to provide relevant feeds of events about the offline world for on-chain usage such as TBC pricing, tokens linked to off-chain factors.

**Proposal Goals (list with explanations where possible)**

Build contracts about outside world data feeds (DEX, decentralized insurance). 
Feeds could be dedicated to the market data, weather info (humidity, temperature, pressure), seismic data, etc. 
The oracles should give relevant feeds of relatively small events about the offline world for on-chain usage such as TBC pricing, tokens linked to off-chain factors.

**Scope of Work (describe the scope of work in as much detail as possible)**

Feeds differ from each other by:

	+ provider

	+ event members (length of the event “data tuple“)

	+ update period

	+ aggregation strategy

	+ public / with authorization. Fetching data for public feeds is mandatory for the oracles. Fetching data for limited-access feeds (with website authorization, )


Every owner of the Sora node is able to become the oracle once they have enough money for staking.
Every oracle should use their controller account to sign the observations. 
Network validator approach can be precisely followedand account should own a controller account (for on-chain configuration) and stash account (for rewards).
The oracle should listen to several data sources (e.g. CEXs) via HTTP or WS. API keys (credentials) are part of node configuration which is done via RPC call setup_oracle.

Oracle is obliged to stay online and gather required observations (without credentials). 
For multiple conflicting reports we use simple median consensus.
Roles are: 

	+ Oracle node - standard node broadcasting all gathered observations.

	+ Leader node - specific oracle node chosen for epoch, controls rounds in which it gathers observations from another oracles.

	+ Submitter node - multiple nodes for epoch, use pseudo-random time-off mechanism to submit final report. (one report is sufficient, therefore on successful submission other submitters skip)

The following steps should be followed to generate reports:

	1 VRF assigns (primary) slots for block producer(s), actual block producer is considered a leader which will submit aggregated report.

	2 Oracle nodes match active validator set for given epoch, act as requesters collect data from defined sources, individual observations are signed and broadcasted among validators network.

	3 Leader collects observations, produces the report and broadcasts it. Oracle nodes provide cross signature for given report, signatures are collected by leader.

	4 Final report is submitted by leader, it contains signed observations and their issuing accounts, cross signatures for whole report.

	5 Observations are aggregated: median is used to find consensus value, outliers are marked and their stake is slashed.

Outlier detection should be implemented to detect faulty nodes, Different data types can have different approaches to deriving consensus value, i.e. different aggregation algorithms. Examples are: median for price value, majority for enum value. Therefore those models should as well define outliers detection mechanism.

To achieve that clustering algorithms can be utilized, e.g. k-means for detecting groups of outliers or simplified approach like threshold cut from mean value.

An oracle node should be able to send messages to all other oracle nodes, not directly accesible in offchain workers. Getting the network state of node - connected peer and manually communicating with them as per https://docs.rs/sc-network/0.9.0/sc_network/struct.NetworkWorker.html#method.network_state is promising but not recommended. 

Slow or malicious oracles should be slashed with some fixed amount of XOR. 
Criteria for oracles to be slashed is:
	
	+Oracles whose observations are systematically not being included in the report (e.g. because they send invalid observations e.g. bad signature, wrong timestamp; oracle set = validators set)
	+Oracles whose observations' cross-signatures are systematically not being included
	+Oracles whose observations systematically differ from consensus value
	+Oracles whose observations are systematically slow (otherwise there’s no reason to actually gather information, they can just retransmit data from others' observations)
	Oracle client mechanisms should provide fees, e.g. there’s burned fee in TBC at the moment, it can be directed for oracles usage.

For every successful on-chain report the fee is distributed after the dispute period among:
	
	+Observations' authors
	+Cross-signers

Data format for on-chain logic should be:

struct OraclesReport {
    // Byproduct of self-signing from each oracle
    observations: Map<AccountId, (Observation, Signature)>,
    signatures: Map<AccountId, Signature>, // Byproduct of oracles' cross-signing
}

struct Observation {
    timestamp: u64,
    events: Vec<FeedEvent>,
}

struct FeedEvent {
    feed_id: FeedId,
    // Will be used to match observations, can be verified on-chain
    // (should keep the update period)
    timestamp: u64, 
    members: Vec<u128>,
}

type AggregatedPrice = Balance;

enum ProviderSpec {
    Http {
        url: String, // HTTP or HTTPS
        auth: Option<ProviderAuthSpec>,
    },
    Ws {
        url: String, // WS or WSS
        start_message: Option<String>,
        auth: Option<ProviderAuthSpec>,
    },
    //PressureSensor,
    //SeismicSensor,
}

enum ProviderAuthSpec {
    HttpHeader { name: String },
    QueryParameter { name: String },
    //FormUrlencodedField { name: String },
    //AuthMessage { pattern: String },
}

struct FeedEventMemberSpec {
    name: String,
    precision: u8,
    extraction: FeedEventMemberExtractor,
}

enum FeedEventMemberExtractor {
    JsonPath { path: String },
    //FormUrlencodedField { name: String },
    //Protobuf { schema, .. },
    //Fix { .. },
    //Fast { .. },
}

enum AggregatorSpec {
    OutlierRemoving { events: u32, percentile },
    SlidingAverage { events: u32 },
}

With Storage Layout
	StorageMap feeds (FeedId) → Vec<u128>
	main storage for current feeds' state
	StorageMap relevantPrices (TradingPair) → AggregatedPrice
	dedicated map for prices
	StorageValue enabledPairs → Set<(Provider, TradingPair)>
	set of pairs to observe

Extrinsics are:

+ create_feed(
    name: String,
    provider: ProviderSpec,
    pair: Option<TradingPair>,
    members: Vec<FeedEventMemberSpec>,
    update_period_s: u32,
    aggregator: Option<AggregatorSpec>,
) - [ROOT] Creates or edits data feed with specified name. Supposed to be applied via referendum.
+ update_feeds(report) - submitter sends final report;
+ set_feed_data(feed_id, timestamp: u64, market_data: Vec<Vec<u128>>) - [ROOT] apply dispute, sets the “correct market data” for the specified set of events. Could be performed only within “dispute interval” for particular submitted events. Supposed to be applied via referendum.

There should be a way to synchronize Sora network updates with requesters’ updates because they both can change their APIs. As the off-chain features are declared in the same code as the runtime, they can be deployed by the same runtime upgrade mechanism we typically use.
Oracle’s configuration should be kept in its local storage to be available in the offchain worker after the runtime upgrade without additional RPC calls.

**Current Roadblocks and Barriers to Success**

On-chain liquidity sources are prone to flash loan manipulation, low market coverage, and sometimes stale price updates. 
Other risks listed here https://medium.com/bandprotocol/why-defi-needs-real-oracles-beyond-dex-9c80cf192883

This issue becomes more apparent for lower-liquidity assets, whose
market price can be shifted with lower amounts of capital.

**Evaluation Metrics and Criteria (definition of done should be as clear as possible)**
Oracle functionalities are accessible within the SORA ecosystem, logic
implemented within SORA repository

**Submission Requirements**

Fulfill evaluation metrics and criteria.
Pull requests to paths as outlined within Submission Method done before Due Date.

**Submission Method (which folder on GitHub to submit a proposal to)**
https://github.com/sora-xor/rfps/tree/master/open_rfps

**Project Due Date**
September 2022

**Budget Amount**
