---
author: ["Chris Achinga"]
title: "Blockchain Oracles"
date: "2025-05-26"
description: "You can build your apps on blockchain"
tags: ["blockchain"]
ShowToc: true
---

I have been working with an organization, Green World Campaign Kenya to build AIRs—Automated Incentives for Regenerative Stewardship - empowering Kenyan farmers with cutting-edge fintech to restore ecosystems and livelihoods.

The project's mission is basically to incentivize regenerative land stewardship in Kenya through a transparent, tech-driven system that rewards farmers, combats climate change, and uplifts rural communities.

https://www.airsgreenworld.com/about

## The Fear

Building on a blockchain has been scary to me, at least that's what I thought. I had already designed and built an architecture that handles data collection, verification and storage, on what some people may call it "web 2" technologies, and I did not feel the need to re-write everything in smart contracts again ... 

In mind I was hoping for a way to bridge in the two worlds, "web 2" and "web 3". Basically where I have smart contracts running on external data sources(APIs). I thought that was just theory, then ...

## Oracles
>Blockchain oracles are entities that connect blockchains to external systems, thereby enabling smart contracts to execute based upon inputs and outputs from the real world. - re write

### Understanding smart contracts

These are programs/software running on a blockchain network. Which like any other code written, checks if defined conditions are met to execute a trigger/action. These programs run on a decentralized network and they can allow multiple parties to execute and have shared results.

>Not all blockchains can run smart contracts.

## Oracle Network
Oracles provide a way for the decentralized Web3 ecosystem to access existing data sources, legacy systems, and advanced computations. Decentralized oracle networks (DONs) enable the creation of hybrid smart contracts, where onchain code and offchain infrastructure are combined to support advanced decentralized applications (dApps) that react to real-world events and interoperate with traditional systems.
Solving the oracle problem is of the utmost importance because the vast majority of smart contract use cases like DeFi require knowledge of real-world data and events happening offchain. Thus, crypto oracles expand the types of digital agreements that blockchains can support by offering a universal gateway to offchain resources while still upholding the valuable security properties of blockchains. Major industries benefit from combining oracles and smart contracts including asset prices for finance, weather information for insurance, randomness for gaming, IoT sensors for supply chain, ID verification for government, and much more.

Because the data delivered by oracles to blockchains directly determines the outcomes of smart contracts, it is critically important that the oracle mechanism is correct if the agreement is to execute exactly as expected.

Blockchain oracle mechanisms using a centralized entity to deliver data to a smart contract introduce a single point of failure, defeating the entire purpose of a decentralized blockchain application. If the single oracle goes offline, then the smart contract will not have access to the data required for execution or will execute improperly based on stale data.

Even worse, if the single oracle is corrupted, then the data being delivered onchain may be highly incorrect and lead to smart contracts executing very wrong outcomes. This is commonly referred to as the “garbage in, garbage out” problem where bad inputs lead to bad outputs. Additionally, because blockchain transactions are automated and immutable, a smart contract outcome based on faulty data cannot be reversed, meaning user funds can be permanently lost. Therefore, centralized oracles are a non-starter for smart contract applications.

Truly overcoming the crypto oracle problem necessitates decentralized oracles to prevent data manipulation, inaccuracy, and downtime. A Decentralized Oracle Network, or DON for short, combines multiple independent oracle node operators and multiple reliable data sources to establish end-to-end decentralization.

DONs enable the creation of hybrid smart contracts, where onchain code and offchain infrastructure are combined to support advanced decentralized applications (dApps) that react to real-world events and interoperate with traditional systems.

Many Chainlink services, such as Chainlink Price Feeds, incorporate three layers of decentralization—at the data source, individual node operator, and oracle network levels—to eliminate any single point of failure. Chainlink Price Feeds already help secure tens of billions of dollars across smart contract ecosystems through this multi-layered decentralization approach, ensuring smart contracts can safely rely on data inputs during their execution.

Types of Blockchain Oracles

Given the extensive range of offchain resources, blockchain oracles come in many shapes and sizes. Not only do hybrid smart contracts need various types of external data and computation, but they require various mechanisms for delivery and different levels of security. Generally, each type of crypto oracle involves some combination of fetching, validating, computing upon, and delivering data to a destination.

Input Oracles

The most widely recognized type of oracle today is known as an “input oracle,” which fetches data from the real-world (offchain) and delivers it onto a blockchain network for smart contract consumption. These types of oracles are used to power Chainlink Price Feeds, providing DeFi smart contracts with onchain access to financial market data.

Output Oracles

The opposite of input oracles are “output oracles,” which allow smart contracts to send commands to offchain systems that trigger them to execute certain actions. This can include informing a banking network to make a payment, telling a storage provider to store the supplied data, or pinging an IoT system to unlock a car door once the onchain rental payment is made.

Cross-Chain Oracles

Another type of oracle are cross-chain oracles that can read and write information between different blockchains. Cross-chain oracles enable interoperability for moving both data and assets between blockchains, such as using data on one blockchain to trigger an action on another or bridging assets cross-chain so they can be used outside the native blockchain they were issued on.

Compute-Enabled Oracles

A new type of oracle becoming more widely used by smart contract applications are “compute-enabled oracles,” which use secure offchain computation to provide decentralized services that are impractical to do onchain due to technical, legal, or financial constraints. This can include using Chainlink Automation to trigger the running of smart contracts when predefined events take place, computing zero-knowledge proofs to generate data privacy, or running a verifiable randomness function to provide a tamper-proof and provably fair source of randomness to smart contracts.

-- https://chain.link/education/blockchain-oracles#what-is-an-oracle-network

What Is the Oracle Problem?

The oracle problem revolves around a very simple limitation—blockchains cannot pull in data from or push data out to any external system as built-in functionality. As such, blockchains are isolated networks, akin to a computer with no Internet connection. The isolation of a blockchain is the precise property that makes it extremely secure and reliable, as the network only needs to form consensus on a very basic set of binary (true/false) questions using data already stored inside of its ledger. These questions include: did the public key holder sign the transaction with their corresponding private key, does the public address have enough funds to cover its transaction, and is the type of transaction valid within the particular smart contract? The very narrow focus of blockchain consensus is why smart contracts are referred to as being deterministic—they execute exactly as written with a much higher degree of certainty than traditional systems.

However, for smart contracts to realize upwards of 90% of their potential use cases, they must connect to the outside world. For example, financial smart contracts need market information to determine settlements, insurance smart contracts need IoT and web data to make decisions on policy payouts, trade finance contracts need trade documents and digital signatures to know when to release payments, and many smart contracts want to settle in fiat currency on a traditional payment network. None of this information is inherently generated within the blockchain, nor are these traditional services directly accessible.

Bridging the connection between the blockchain (on-chain) and the outside world (off-chain) requires an additional and separate piece of infrastructure known as an oracle.

What Is a Blockchain Oracle?

A blockchain oracle is a secure piece of middleware that facilitates communication between blockchains and any off-chain system, including data providers, web APIs, enterprise backends, cloud providers, IoT devices, e-signatures, payment systems, other blockchains, and more. Oracles take on several key functions:

Listen – monitor the blockchain network to check for any incoming user or smart contract requests for off-chain data.
Extract – fetch data from one or multiple external systems such as off-chain APIs hosted on third-party web servers.
Format – format data retrieved from external APIs into a blockchain readable format (input) and/or making blockchain data compatible with an external API (output).
Validate – generate a cryptographic proof attesting to the performance of an oracle service using any combination of data signing, blockchain transaction signing, TLS signatures, Trusted Execution Environment (TEE) attestations, or zero-knowledge proofs.
Compute – perform some type of secure off-chain computation for the smart contract, such as calculating a median from multiple oracle submissions or generating a verifiable random number for a gaming application.
Broadcast – sign and broadcast a transaction on the blockchain in order to send data and any corresponding proof on-chain for consumption by the smart contract.
Output (optional) –  send data to an external system upon the execution of a smart contract, such as relaying payment instructions to a traditional payment network or triggering actions from a cyber-physical system.
Carrying out the functions above requires that the oracle system operate both on and off the blockchain simultaneously. The on-chain component is for establishing a blockchain connection (to listen for requests), broadcasting data, sending proofs, extracting blockchain data, and potentially performing computation on the blockchain. The off-chain component is for processing requests, retrieving and formatting external data, sending blockchain data to external systems, and performing off-chain computation for greater scalability, privacy, security, and various other smart contract enhancements.

Why Blockchains Can’t Solve the Oracle Problem

Blockchains are highly secure and reliable because of a few specific design principles. As described above, a blockchain only needs to form consensus on very basic binary questions using data already stored on its own ledger. The blockchain’s ledger is deemed to be true because it leverages decentralization to redundantly validate every piece of data using all the nodes in the network. It also uses decentralization to maintain the integrity of its consensus algorithm (PoW, PoS, etc.), ensuring the protocol rules only change when a substantial portion of the network signs off on it (e.g., 51%). These properties provide strong guarantees of computational and data storage determinism, especially in highly decentralized and Sybil-resistant networks.

However, blockchains are not well suited to answer questions that delve into the realm of subjectivity or require external data that is not easily accessible to every node in the network. For example, a simple question like ‘What is the market price of Bitcoin?’ or ‘What is the weather in New York?’ can elicit a wide range of different answers that may vary depending on what data source they use and when they request data from the source. The question then becomes, what is the correct answer and how can it be verified as true?

Introducing subjectivity at the base layer of the blockchain opens up Pandora’s box to a whole host of security, reliability, and governance concerns, putting at risk the very value proposition blockchains aim to provide.

One major concern is how to ensure external data inputted into the blockchain is high quality? Even a basic data request for the price of Bitcoin is quite challenging because simply looking at a website or a single exchange may not be as accurate or reliable as a paid API subscription to a professional data aggregator that has decades of experience filtering data and creating market coverage and is financially incentivized to maintain high-quality services. It’s extremely difficult to manage and enforce quality for off-chain data submitted by blockchain nodes since anyone can pseudo-anonymously run a node and submit answers, even if they are not willing to buy a subscription to a high-quality off-chain API. If data quality was enforced, the blockchain would then have a lower upper bound on decentralization since the costs of running nodes would increase for every new oracle job on the network, affecting the security of all other applications running on the particular blockchain.

-- https://chain.link/education-hub/oracle-problem

What is a blockchain oracle in crypto?

Blockchain oracles are entities that connect blockchains to external systems, enabling smart contracts to execute based on real-world inputs and outputs.
Oracles play an important role in the creation of the verifiable web, connecting isolated blockchains to off-chain data and compute, and enabling interoperability between blockchains.
Blockchain oracles are not the data source themselves, but rather the layer that queries, verifies, and authenticates external data sources and then relays that information.
Understanding Blockchain Oracles
Blockchain oracles are third-party services that provide smart contracts with external information. They serve as bridges between blockchains and the outside world. Blockchains and smart contracts cannot access off-chain data (data that is outside of the network). However, for many contractual agreements, it is necessary to have relevant information from the outside world to execute the agreement.
This is where blockchain oracles come into play, as they provide a link between off-chain and on-chain data. Oracles are important within the blockchain ecosystem because they broaden the scope in which smart contracts can operate. Without blockchain oracles, smart contracts would have very limited use as they would only have access to data from within their networks.
How Blockchain Oracles Work
Blockchain oracles are not the data source themselves, but rather the layer that queries, verifies, and authenticates external data sources and then relays that information. The data transmitted by oracles comes in many forms – price information, the successful completion of a transaction, or the temperature measured by a sensor.
To call data from the outside world, the smart contract has to be invoked, and network resources have to be spent. Some oracles also have the ability to not only relay information to smart contracts but to send it back to external sources.
Types of Blockchain Oracles
There are several types of blockchain oracles, each designed to serve a specific purpose. Software oracles aggregate data available on the internet and feed it to a smart contract, such as price data for digital assets. Hardware oracles reference data from the physical world, which can only come through a piece of hardware such as a sensor or scanner. Human oracles involve a person providing data based on real-world events.
The Oracle Problem
The blockchain oracle problem highlights a key restriction of smart contracts, i.e., they cannot connect with data and systems outside of their native blockchain context. This limitation is due to the deterministic nature of blockchain architecture, where each node in the network must obtain the same result given the same input. This deterministic architecture is important for nodes to reach a consensus, a fundamental aspect of blockchain functionality.
Blockchain Oracle Use Cases
Blockchain oracles have a variety of use cases. They are used in decentralized finance (DeFi) to provide current price data of digital assets. They are also used in betting and prediction markets, gaming, non-fungible tokens (NFTs), and insurance. In each of these cases, oracles provide an important link between the blockchain and real-world data, enabling smart contracts to function effectively.

-- https://www.coinbase.com/learn/crypto-glossary/what-is-a-blockchain-oracle-in-crypto

From Wikipedia, the free encyclopedia
A blockchain oracle is a third-party service for smart contracts. Oracles provide trusted information based on the outside-world sources to the on-blockchain smart contracts. An oracle typically encapsulates the real-world complexity outside of the blockchain. This provides different engineering advantages, chiefly that critical errors and potential points of failure are easier to mitigate off-chain than on-chain.[1]

For example, in a contract to automatically purchase bitcoins at a predetermined price, the fulfillment condition is based on the current exchange rate for the bitcoin; an off-chain oracle can constantly monitor the price to provide the triggering condition to the contract.[2]

Examples
Kustov and Selanteva list the following types of oracles:[2]

a program, external to the blockchain that can provide, for example, sports results for betting or traffic camera information for ticketing the offenders;
a unit oracle that is built-in into a physical sensor (for example, the same traffic camera);
an entry oracle executes the code that is actually stored on-chain and provides the result (say, the bitcoin price matching the condition) as an input to the contract;
an exit oracle handles the results of the smart contract (for example, paying a fee) by manipulating a real-world device (say, opening a door). It code can also be stored on-chain;
an oracle agreement is an aggregator of many oracles to determine the condition when the real-world oracles disagree.
Concerns
If an oracle relies on a single source of truth (centralized), that can lead to issues: the data source can be hacked in a man-in-the-middle attack, or altered by its owner, in order to sway smart contracts. Decentralized oracles (consensus oracles) increase the reliability of the information provided to smart contracts by querying multiple data sources, thus distributing trust between participants. However, this does not achieve trustlessness, since oracles are not part of the main blockchain consensus, and thus not part of the security mechanisms of public blockchains.[3]

-- https://en.wikipedia.org/wiki/Blockchain_oracle

Smart Contract Building Blocks

ORACLES
A blockchain oracle facilitates the execution of smart contracts by providing real-world input and output data.


What is an Oracle?
A blockchain oracle is an entity that enables smart contracts, autonomous pieces of code that self-execute once conditions are met, to execute based on inputs and outputs from the real world. Oracles connect blockchains to external systems, like data sources and other off-chain networks, feeding information from these external systems into smart contracts that rely on specific, real-world conditions. By sourcing, verifying, and transmitting external information to smart contracts on a blockchain, oracles function as bridges between on- and off-chain infrastructure.
Why are oracles important?
By nature, blockchains and smart contracts that run on a blockchain network are intentionally separate from external systems. This means that smart contracts are fundamentally limited and cannot interact with systems outside their own blockchain environments. As the necessary bridge to off-chain resources for smart contracts, oracles must service the blockchain with trustworthy and reputable data, while still upholding the values afforded by decentralization.
How do oracles work?
An oracle integrates with a given chain via a smart contract, which operates as the user of the oracle. When the user (smart contract) sends its data request to the oracle, the oracle’s on-chain component (oracle contract) queries that data by connecting to external data sources via the oracle’s off-chain component (oracle node) and extracting the necessary information. The oracle then returns the queried data from the source to the smart contract on the blockchain. Oracles can function cross-chain, meaning that they may serve data to not just one but multiple chains, by integrating with those chains.
Types of Oracles
There are numerous types of oracles, each with their own functions and capabilities.

‍Software oracles are the most common, pulling data from third-party sources like web APIs, such as weather or financial data. There are two types of software oracles. Input oracles request data from real-world, off-chain sources and broadcast this data to the blockchain. Use cases include triggering a function in a smart contract if a certain real-world condition is met. Output oracles allow smart contracts to send data or commands to systems outside the blockchain network they exist on, or off-chain entirely. For instance, a smart contract might use an output oracle to request that a banking network make a payment; or to unlock a home or car door via an Internet of Things (IoT) system once an on-chain rental payment has been made.

‍Hardware oracles use IoT sensors integrated with physical objects. They may be used for supply chain management via radio frequency identification (RFID) to broadcast data related to supply chain products to the blockchain.

‍Cross-chain oracles allow smart contracts to read and write data between blockchains, enabling interoperability by transferring data or assets from one blockchain to another, triggering an action on one blockchain from another, or bridging assets cross-chain so that they can be used outside the native blockchain they were issued on.

‍Compute-enabled oracles use a secure, off-chain computation system to provide decentralized services that may be impractical on the blockchain due to technical, legal, financial, or privacy constraints.
The Range

LEVELS OF DECENTRALIZATION
The types of oracles listed above can be implemented in ways that range from fully centralized to fully decentralized.

‍Centralized oracles are controlled by a single entity that aggregates off-chain data and updates the oracle’s data as requested. While centralized oracles can be efficient because they depend only on one source, they don’t benefit from the value of decentralization since they may be susceptible to manipulation, censorship, or hacks, and constitute a single point of failure if the oracle goes offline, and smart contracts, whose functions depend on that data, will not be able to execute or may execute inaccurately.

‍Consensus-based oracles utilize the data from several other oracles. While not quite single-source or centralized, these oracles are also not decentralized, as they still rely on the authenticity and accuracy of those other oracle sources. Semi-decentralized, consensus-based oracles may allow anyone to participate in validating off-chain data but will still rely on an owner to approve the consensus.

‍Decentralized oracles, unlike centralized oracles, are designed to eliminate single points of failure. A decentralized oracle relies on multiple participants in a peer-to-peer network to form a consensus on off-chain data before that data is broadcasted to a smart contract on the blockchain. At their best, decentralized oracles are permissionless, trustless, and free from administration governance by any individual entity, utilizing authenticity proofs to guarantee the high correctness of the data they are sending to the blockchain.
The "Oracle Problem"
The biggest challenge faced by oracles, known as the “Oracle Problem,” is how to make sure that the data oracles source from third parties guarantees the following crucial qualities:

‍Correctness: smart contracts should not execute on invalid off-chain data;

‍Authenticity: oracles must guarantee that the data comes from the correct source;

‍Integrity: the data must be intact and unaltered;

‍Trustlessness: oracles must reliably provide accurate data without needing the trust of a third party that might otherwise result in a single point of failure;

‍Availability: there should be no interruptions or delays in broadcasting data to the blockchain via an oracle, prohibiting a smart contract from executing.

Decentralized oracle solutions, which leverage consensus-based oracles, decentralized marketplaces, and various data authentication methods, work to minimize data manipulation, oracle failure, and the problem of trust. In addition to improving decentralized oracles, oracle service providers employ various strategies to enhance oracle security, from developing data verification and aggregation techniques; to improving consensus mechanisms and oracle designs; to implementing cryptographic proofs and auditing mechanisms; to exploring reputation systems that increase the transparency of the oracle network and each individual node operator in that network.
Oracle Use Cases
Oracles enable smart contracts to tap into decentralized, tamper-proof sources across industries, including:

‍Decentralized finance (DeFi), where price oracles are used in ecosystems to access financial data about assets and markets, including exchange rates and capital market data; to determine users’ lending and borrowing capacities; to fix the value of blockchain tokens against real-world assets; and to concentrate liquidity pools around the current market price to efficiently maximize returns.
Future Trends
As a core building block of smart contracts and blockchain technologies, oracles are powerful tools that have the potential to impact not only the uses of blockchains and smart contracts in existing industries but also the broader adoption of blockchain technologies across new and developing industries.

With the emergence and increasing adoption of technologies like artificial intelligence, machine learning, and IoT devices, oracle integrations that connect Web3 infrastructure and smart contracts in decentralized finance beyond today’s capabilities.

-- https://stellar.org/learn/smart-contract-basics-oracles


Summary of blockchain oracles
Developers often program smart contracts to activate when certain real-world events take place
Oracles automatically provide that real-world information to the blockchain without human involvement
Incorporating off-chain data allows decentralized applications (dApps) to deliver a much wider variety of user experiences, such as trading, prediction markets, gambling and more
What is a blockchain oracle?
Oracles provide blockchains and smart contracts with real-world data that otherwise would not exist on the blockchain.
Because blockchains are purpose-built to track information stored on their networks, they can have a hard time accessing information from the “real-world” that does not originate from the blockchain itself.
By allowing blockchains to gain access to real-world data, oracles allow developers to create a broader range of decentralized applications (dApps).
Each dApp consists of smart contracts — pieces of computer code that execute certain functions when predetermined conditions are met. These work similarly to the services the apps on your smartphone provide, but without relying on any human intermediaries.
Blockchains can be isolated networks that do not have direct access to real-world events or conditions. Oftentimes, blockchains can only access data that already exists on their networks and therefore cannot access data that isn't directly created and stored on-chain.
By feeding real-world data, such as stock prices or the outcomes of sporting matches, into smart contracts, developers can significantly expand the functionality of the applications they create.
For example, using an oracle service, a developer could create a decentralized prediction market application.
Using smart contracts, the application would allow users to speculate on the outcome of any future event with other people worldwide. These could include bets on which country will win the next FIFA World Cup, who will win the next American Presidential election or any other outcome of the developer’s choosing.
Using real-world data from oracles, the prediction market could automatically settle bets without requiring a human intermediary to approve who won.
Why are oracles important?
Without oracles to provide access to off-chain data, blockchain networks would have no access to information like stock market prices, user identity data, sports scores, the weather, transactions on other blockchains and much more.
Instead, blockchain would likely require human involvement to provide the information. This leads to centralization risk, which would undermine one of the key differentiators for blockchain networks: decentralization.
Many decentralized finance (DeFi) protocols could not exist without oracles and their ability to bring data onto source information while still remaining decentralized .
Lending protocols like Aave (AAVE) that allow users to lend and borrow tokens require close monitoring of token prices to function. If these prices could be manipulated by a single individual, it would ruin the decentralized nature of the protocol.
Trading protocols like dYdX (DYDX) rely on oracles to return price feeds for tradable assets. If these price feeds were only supplied by a single individual or company, the trading service would entirely rely on this centralized feed to operate its decentralized trading platform.
Gambling protocols like Augur v2 (REPV2) need oracles to retrieve sports scores. If the protocol did not rely on the consensus of the network as to the outcome of a particular match, but instead relied on a single individual to provide the outcome, the protocol would rely on a single source of truth that could be subject to manipulation.
Ultimately, oracles play an important role in connecting the decentralized world of blockchain technology to events in the physical world. While we have historically relied on centralized, “trusted” intermediaries to perform this duty in the past, oracles offer a more transparent and tamper resistant way of verifying outcomes.
Get started
How does a blockchain oracle work?
An oracle has two components:
An on-chain smart contract
An oracle network
If a dApp needs real-world data from an oracle, the dApp’s developers connect its smart contract to the oracle’s smart contract. The oracle’s smart contract monitors the linked dApp smart contract for off-chain data requests.
When a dApp’s smart contract requests off-chain data, such as the outcome of a certain event the oracle’s smart contract passes that data request to the oracle network.
An oracle network is a set of computers that cooperate to find and verify data. After they find that data, reach consensus on its validity, and reform the data to be blockchain-readable, the network passes that data to the oracle smart contract.
Finally, the oracle smart contract passes the data back to the original smart contract to execute and validate the initial transaction with the additional context provided by the off-chain data from the oracle.
Trade-offs of blockchain oracles
While DeFi oracles can be helpful, they require dApps that use them to make certain trade-offs.
Some protocols receive praise for being "oracle-free" and not relying on oracles for information. Blockchain users who grasp the trade-offs of oracle networks can better understand DeFi and better evaluate DeFi tokens.
Attack vectors
Blockchains often remain isolated for a reason — to keep their data safe.
Allowing oracles to bring outside data on-chain carries certain risks.
Many oracles use proprietary infrastructure and networks (for example, the three layers of decentralization in Chainlink Price Feeds) to secure and transmit data.
Hackers can attack this infrastructure in ways they can’t attack blockchains. So, while oracles can add helpful information to a blockchain ecosystem, they also have the potential to make it less secure if the network is facing a coordinated attack.
Data manipulation
There are many ways oracle attacks can hurt users through data manipulation.
For example, a hacker could manipulate an oracle to report the wrong Bitcoin price to a decentralized market. In that case, traders may buy or sell at a loss relative to the correct market price.
Similarly, incorrect price information may trigger loan defaults and liquidations on decentralized lending and yield farming platforms.
Inaccurate information about sporting events can trigger wrongful payouts on gambling dApps. User losses from this kind of manipulated data can be triggered suddenly and be costly to users.
In 2022, a well-known DeFi platform on the Solana blockchain called Mango Markets (MNGO) was exploited due to oracle manipulation.
The hacker first artificially drove the price of the native token, MNGO, up nearly 30x. Then, the hacker drained the protocol of its funds by taking out massive loans using the artificially-inflated MNGO token as collateral.
The oracle was receiving a bad input via an inflated token price, which had the side effect of incorrectly assuming the hacker’s collateral was worth significantly more than it actually was.
How to limit oracle risk
Some oracles are riskier than others. For example, smaller or newer oracle networks may be more vulnerable to attack than larger and comparatively older ones that have been reliable over time.
Newer oracle networks may have battle-tested infrastructure, which may leave some questioning if there are undiscovered points of vulnerability.
One way to limit oracle risks is to engage with protocols that either don’t use oracles or use oracle networks that have a demonstrated track record of being reliable.
Uniswap (UNI) is a top example of a DeFi protocol that doesn't use an oracle and thus has the security benefit of being "oracle-free."
Due to the nature of liquidity pools and how they price assets, Uniswap doesn't rely on external pricing data. Instead, Uniswap is able to generate all of the data  it needs to function directly from its own smart contracts.
Popular blockchain oracles
While no oracle is guaranteed to be safe against cyber attacks, there are several leading services that many DeFi traders and protocols use:
Chainlink (LINK) is DeFi’s foremost oracle network, enabling over tens of trillion of dollars in transactions to date. Chainlink offers a variety of products, including the Cross-Chain Interoperability Protocol, a robust network for transmitting data between different blockchains. Check out our Kraken Learn Center article What is Chainlink? to learn more about how this protocol works.

-- https://www.kraken.com/learn/blockchain-oracles

ORACLES

(opens in a new tab)
Last edit: @wackerow(opens in a new tab), February 12, 2025
See contributors
Oracles are applications that produce data feeds that make offchain data sources available to the blockchain for smart contracts. This is necessary because Ethereum-based smart contracts cannot, by default, access information stored outside the blockchain network.

Giving smart contracts the ability to execute using offchain data extends the utility and value of decentralized applications. For instance, onchain prediction markets rely on oracles to provide information about outcomes that they use to validate user predictions. Suppose Alice bets 20 ETH on who will become the next U.S. President. In that case, the prediction-market dapp needs an oracle to confirm election results and determine if Alice is eligible for a payout.

PREREQUISITES

This page assumes the reader is familiar with Ethereum fundamentals, including nodes, consensus mechanisms, and the EVM. You should also have a good grasp of smart contracts and smart contract anatomy, especially events.

WHAT IS A BLOCKCHAIN ORACLE?

Oracles are applications that source, verify, and transmit external information (i.e. information stored offchain) to smart contracts running on the blockchain. Besides “pulling” offchain data and broadcasting it on Ethereum, oracles can also “push” information from the blockchain to external systems, e.g., unlocking a smart lock once the user sends a fee via an Ethereum transaction.

Without an oracle, a smart contract would be limited entirely to onchain data.

Oracles differ based on the source of data (one or multiple sources), trust models (centralized or decentralized), and system architecture (immediate-read, publish-subscribe, and request-response). We can also distinguish between oracles based on whether they retrieve external data for use by onchain contracts (input oracles), send information from the blockchain to the offchain applications (output oracles), or perform computational tasks offchain (computational oracles).

WHY DO SMART CONTRACTS NEED ORACLES?

Many developers see smart contracts as code running at specific addresses on the blockchain. However, a more general view of smart contracts is that they are self-executing software programs capable of enforcing agreements between parties once specific conditions are met - hence the term “smart contracts.”

But using smart contracts to enforce agreements between people isn't straightforward, given that Ethereum is deterministic. A deterministic system(opens in a new tab) is one that always produces the same results given an initial state and a particular input, meaning there is no randomness or variation in the process of computing outputs from inputs.

To achieve deterministic execution, blockchains limit nodes to reaching consensus on simple binary (true/false) questions using only data stored on the blockchain itself. Examples of such questions include:

“Did the account owner (identified by a public key) sign this transaction with the paired private key?”
“Does this account have enough funds to cover the transaction?”
“Is this transaction valid in the context of this smart contract?”, etc.
If blockchains received information from external sources (i.e. from the real world), determinism would be impossible to achieve, preventing nodes from agreeing on the validity of changes to the blockchain’s state. Take for example a smart contract that executes a transaction based on the current ETH-USD exchange rate obtained from a traditional price API. This figure is likely to change frequently (not to mention that the API could get deprecated or hacked), meaning nodes executing the same contract code would arrive at different results.

For a public blockchain like Ethereum, with thousands of nodes around the world processing transactions, determinism is critical. With no central authority serving as a source of truth, nodes need mechanisms for arriving at the same state after applying the same transactions. A case whereby node A executes a smart contract’s code and gets "3" as a result, while node B gets "7" after running the same transaction would cause consensus to break down and eliminate Ethereum’s value as a decentralized computing platform.

This scenario also highlights the problem with designing blockchains to pull information from external sources. Oracles, however, solve this problem by taking information from offchain sources and storing it on the blockchain for smart contracts to consume. Since information stored onchain is unalterable and publicly available, Ethereum nodes can safely use the oracle imported offchain data to compute state changes without breaking consensus.

To do this, an oracle is typically made up of a smart contract running onchain and some offchain components. The onchain contract receives requests for data from other smart contracts, which it passes to the offchain component (called an oracle node). This oracle node can query data sources—using application programming interfaces (APIs), for example—and send transactions to store the requested data in the smart contract's storage.

Essentially, a blockchain oracle bridges the information gap between the blockchain and the external environment, creating “hybrid smart contracts”. A hybrid smart contract is one that functions based on a combination of onchain contract code and offchain infrastructure. Decentralized prediction markets are an excellent example of hybrid smart contracts. Other examples might include crop insurance smart contracts that pay out when a set of oracles determine that certain weather phenomena have taken place.

WHAT IS THE ORACLE PROBLEM?

Oracles solve an important problem, but also introduce some complications, e.g.:

How do we verify that the injected information was extracted from the correct source or hasn’t been tampered with?
How do we ensure that this data is always available and updated regularly?
The so-called “oracle problem” demonstrates the issues that come with using blockchain oracles to send inputs to smart contracts. Data from an oracle must be correct for a smart contract to execute correctly. Further, having to ‘trust’ oracle operators to provide accurate information undermines the 'trustless' aspect of smart contracts.

Different oracles offer different solutions to the oracle problem, which we explore later. Oracles are typically evaluated on how well they can handle the following challenges:

Correctness: An oracle should not cause smart contracts to trigger state changes based on invalid offchain data. An oracle must guarantee authenticity and integrity of data. Authenticity means the data was gotten from the correct source, while integrity means the data remained intact (i.e. wasn’t altered) before being sent onchain.
Availability: An oracle should not delay or prevent smart contracts from executing actions and triggering state changes. This means that data from an oracle must be available on request without interruption.
Incentive compatibility: An oracle should incentivize offchain data providers to submit correct information to smart contracts. Incentive compatibility involves attributability and accountability. Attributability allows for linking a piece of external information to its provider, while accountability bonds data providers to the information they give, so they can be rewarded or penalized based on the quality of information provided.
HOW DOES A BLOCKCHAIN ORACLE SERVICE WORK?

Users

Users are entities (i.e., smart contracts) that need information external to the blockchain to complete specific actions. The basic workflow of an oracle service starts with the user sending a data request to the oracle contract. Data requests will usually answer some or all of the following questions:

What sources can offchain nodes consult for the requested information?
How do reporters process information from data sources and extract useful data points?
How many oracle nodes can participate in retrieving the data?
How should discrepancies in oracle reports be managed?
What method should be implemented in filtering submissions and aggregating reports into a single value?
Oracle contract

The oracle contract is the onchain component for the oracle service. It listens for data requests from other contracts, relays data queries to oracle nodes, and broadcasts returned data to client contracts. This contract may also perform some computation on the returned data points to produce an aggregate value to send to the requesting contract.

The oracle contract exposes some functions which client contracts call when making a data request. Upon receiving a new query, the smart contract will emit a log event with details of the data request. This notifies offchain nodes subscribed to the log (usually using something like the JSON-RPC eth_subscribe command), who proceed to retrieve data defined in the log event.

Below is an example oracle contract(opens in a new tab) by Pedro Costa. This is a simple oracle service that can query offchain APIs upon request by other smart contracts and store the requested information on the blockchain:

pragma solidity >=0.4.21 <0.6.0;
contract Oracle {
Request[] requests; //list of requests made to the contract
uint currentId = 0; //increasing request id
uint minQuorum = 2; //minimum number of responses to receive before declaring final result
uint totalOracleCount = 3; // Hardcoded oracle count
// defines a general api request
struct Request {
uint id;                            //request id
string urlToQuery;                  //API url
string attributeToFetch;            //json attribute (key) to retrieve in the response
string agreedValue;                 //value from key
mapping(uint => string) answers;     //answers provided by the oracles
mapping(address => uint) quorum;    //oracles which will query the answer (1=oracle hasn't voted, 2=oracle has voted)
}
//event that triggers oracle outside of the blockchain
event NewRequest (
uint id,
string urlToQuery,
string attributeToFetch
);
//triggered when there's a consensus on the final result
event UpdatedRequest (
uint id,
string urlToQuery,
string attributeToFetch,
string agreedValue
);
function createRequest (
string memory _urlToQuery,
string memory _attributeToFetch
)
public
{
uint length = requests.push(Request(currentId, _urlToQuery, _attributeToFetch, ""));
Request storage r = requests[length-1];
// Hardcoded oracles address
r.quorum[address(0x6c2339b46F41a06f09CA0051ddAD54D1e582bA77)] = 1;
r.quorum[address(0xb5346CF224c02186606e5f89EACC21eC25398077)] = 1;
r.quorum[address(0xa2997F1CA363D11a0a35bB1Ac0Ff7849bc13e914)] = 1;
// launch an event to be detected by oracle outside of blockchain
emit NewRequest (
currentId,
_urlToQuery,
_attributeToFetch
);
// increase request id
currentId++;
}
//called by the oracle to record its answer
function updateRequest (
uint _id,
string memory _valueRetrieved
) public {
Request storage currRequest = requests[_id];
//check if oracle is in the list of trusted oracles
//and if the oracle hasn't voted yet
if(currRequest.quorum[address(msg.sender)] == 1){
//marking that this address has voted
currRequest.quorum[msg.sender] = 2;
//iterate through "array" of answers until a position if free and save the retrieved value
uint tmpI = 0;
bool found = false;
while(!found) {
//find first empty slot
if(bytes(currRequest.answers[tmpI]).length == 0){
found = true;
currRequest.answers[tmpI] = _valueRetrieved;
}
tmpI++;
}
uint currentQuorum = 0;
//iterate through oracle list and check if enough oracles(minimum quorum)
//have voted the same answer as the current one
for(uint i = 0; i < totalOracleCount; i++){
bytes memory a = bytes(currRequest.answers[i]);
bytes memory b = bytes(_valueRetrieved);
if(keccak256(a) == keccak256(b)){
currentQuorum++;
if(currentQuorum >= minQuorum){
currRequest.agreedValue = _valueRetrieved;
emit UpdatedRequest (
currRequest.id,
currRequest.urlToQuery,
currRequest.attributeToFetch,
currRequest.agreedValue
);
}
}
}
}
}
}
Show less
📋 Copy
Oracle nodes

The oracle node is the offchain component of the oracle service. It extracts information from external sources, such as APIs hosted on third-party servers, and puts it onchain for consumption by smart contracts. Oracle nodes listen for events from the onchain oracle contract and proceed to complete the task described in the log.

A common task for oracle nodes is sending a HTTP GET(opens in a new tab) request to an API service, parsing the response to extract relevant data, formatting into a blockchain-readable output, and sending it onchain by including it in a transaction to the oracle contract. The oracle node may also be required to attest to the validity and integrity of submitted information using “authenticity proofs”, which we explore later.

Computational oracles also rely on offchain nodes to perform computational tasks that would be impractical to execute onchain, given gas costs and block size limits. For example, the oracle node may be tasked with generating a verifiably random figure (e.g., for blockchain-based games).

ORACLE DESIGN PATTERNS

Oracles come in different types, including immediate-read, publish-subscribe, and request-response, with the latter two being the most popular among Ethereum smart contracts. Here we briefly describe the publish-subscribe and request-response models.

Publish-subscribe oracles

This type of oracle exposes a “data feed” which other contracts can regularly read for information. The data in this case is expected to change frequently, so client contracts must listen for updates to the data in the oracle’s storage. An example is an oracle that provides the latest ETH-USD price information to users.

Request-response oracles

A request-response setup allows the client contract to request arbitrary data other than that provided by a publish-subscribe oracle. Request-response oracles are ideal when the dataset is too large to be stored in a smart contract’s storage, and/or users will only need a small part of the data at any point in time.

Although more complex than publish-subscribe models, request-response oracles are basically what we described in the previous section. The oracle will have an onchain component that receives a data request and passes it to an offchain node for processing.

Users initiating data queries must cover the cost of retrieving information from the offchain source. The client contract must also provide funds to cover gas costs incurred by the oracle contract in returning the response via the callback function specified in the request.

CENTRALIZED VS. DECENTRALIZED ORACLES

Centralized oracles

A centralized oracle is controlled by a single entity responsible for aggregating offchain information and updating the oracle contract's data as requested. Centralized oracles are efficient since they rely on a single source of truth. They may function better in cases where proprietary datasets are published directly by the owner with a widely accepted signature. However, they bring downsides as well:

Low correctness guarantees

With centralized oracles, there's no way to confirm if the information provided is correct or not. Even "reputable" providers can go rogue or get hacked. If the oracle becomes corrupt, smart contracts will execute based on bad data.

Poor availability

Centralized oracles aren't guaranteed to always make offchain data available to other smart contracts. If the provider decides to turn off the service or a hacker hijacks the oracle's offchain component, your smart contract is at risk of a denial of service (DoS) attack.

Poor incentive compatibility

Centralized oracles often have poorly designed or non-existent incentives for the data provider to send accurate/unaltered information. Paying an oracle for correctness does not guarantee honesty. This problem gets bigger as the amount of value controlled by smart contracts increases.

Decentralized oracles

Decentralized oracles are designed to overcome the limitations of centralized oracles by eliminating single points of failure. A decentralized oracle service comprises multiple participants in a peer-to-peer network that form consensus on offchain data before sending it to a smart contract.

A decentralized oracle should (ideally) be permissionless, trustless, and free from administration by a central party; in reality, decentralization among oracles is on a spectrum. There are semi-decentralized oracle networks where anyone can participate, but with an “owner” that approves and removes nodes based on historical performance. Fully decentralized oracle networks also exist: these usually run as standalone blockchains and have defined consensus mechanisms for coordinating nodes and punishing misbehavior.

Using decentralized oracles comes with the following benefits:

High correctness guarantees

Decentralized oracles attempt to achieve correctness of data using different approaches. This includes using proofs attesting to the authenticity and integrity of the returned information and requiring multiple entities to collectively agree on the validity of offchain data.

Authenticity proofs

Authenticity proofs are cryptographic mechanisms that enable independent verification of information retrieved from external sources. These proofs can validate the source of the information and detect possible alterations to the data after retrieval.

Examples of authenticity proofs include:

Transport Layer Security (TLS) proofs: Oracle nodes often retrieve data from external sources using a secure HTTP connection based on the Transport Layer Security (TLS) protocol. Some decentralized oracles use authenticity proofs to verify TLS sessions (i.e., confirm the exchange of information between a node and a specific server) and confirm that the contents of the session were not altered.

Trusted Execution Environment (TEE) attestations: A trusted execution environment(opens in a new tab) (TEE) is a sandboxed computational environment that is isolated from the operational processes of its host system. TEEs ensure that whatever application code or data stored/used in the computation environment retains integrity, confidentiality, and immutability. Users can also generate an attestation to prove an application instance is running within the trusted execution environment.

Certain classes of decentralized oracles require oracle node operators to provide TEE attestations. This confirms to a user that the node operator is running an instance of oracle client in a trusted execution environment. TEEs prevent external processes from altering or reading an application’s code and data, hence, those attestations prove that the oracle node has kept the information intact and confidential.

Consensus-based validation of information

Centralized oracles rely on a single source of truth when providing data to smart contracts, which introduces the possibility of publishing inaccurate information. Decentralized oracles solve this problem by relying on multiple oracle nodes to query offchain information. By comparing data from multiple sources, decentralized oracles reduce the risk of passing invalid information to onchain contracts.

Decentralized oracles, however, must deal with discrepancies in information retrieved from multiple offchain sources. To minimize differences in information and ensure the data passed to the oracle contract reflects the collective opinion of oracle nodes, decentralized oracles use the following mechanisms:

Voting/staking on accuracy of data
Some decentralized oracle networks require participants to vote or stake on the accuracy of answers to data queries (e.g., "Who won the 2020 US election?") using the network’s native token. An aggregation protocol then aggregates the votes and stakes and takes the answer supported by the majority as the valid one.

Nodes whose answers deviate from the majority answer are penalized by having their tokens distributed to others who provide more correct values. Forcing nodes to provide a bond before providing data incentivizes honest responses since they are assumed to be rational economic actors intent on maximizing returns.

Staking/voting also protects decentralized oracles from Sybil attacks where malicious actors create multiple identities to game the consensus system. However, staking cannot prevent “freeloading” (oracle nodes copying information from others) and “lazy validation” (oracle nodes following the majority without verifying the information themselves).

Schelling point mechanisms
Schelling point(opens in a new tab) is a game-theory concept that assumes multiple entities will always default to a common solution to a problem in absence of any communication. Schelling-point mechanisms are often used in decentralized oracle networks to enable nodes reach consensus on answers to data requests.

An early idea for this was SchellingCoin(opens in a new tab), a proposed data feed where participants submit responses to "scalar" questions (questions whose answers are described by magnitude, e.g., "what is the price of ETH?"), along with a deposit. Users who provide values between the 25th and 75th percentile(opens in a new tab) are rewarded, while those whose values deviate largely from the median value are penalized.

While SchellingCoin doesn’t exist today, a number of decentralized oracles—notably Maker Protocol’s Oracles(opens in a new tab)—use the schelling-point mechanism to improve accuracy of oracle data. Each Maker Oracle consists of an offchain P2P network of nodes ("relayers" and "feeds") who submit market prices for collateral assets and an onchain “Medianizer” contract that calculates the median of all provided values. Once the specified delay period is over, this median value becomes the new reference price for the associated asset.

Other examples of oracles that use Schelling point mechanisms include Chainlink Offchain Reporting(opens in a new tab) and Witnet(opens in a new tab). In both systems, responses from oracle nodes in the peer-to-peer network are aggregated into a single aggregate value, such as a mean or median. Nodes are rewarded or punished according to the extent to which their responses align with or deviate from the aggregate value.

Schelling point mechanisms are attractive because they minimize onchain footprint (only one transaction needs to be sent) while guaranteeing decentralization. The latter is possible because nodes must sign off on the list of submitted responses before it is fed into the algorithm that produces the mean/median value.

Availability

Decentralized oracle services ensure high availability of offchain data to smart contracts. This is achieved by decentralizing both the source of offchain information and nodes responsible for transferring the information onchain.

This ensures fault-tolerance since the oracle contract can rely on multiple nodes (who also rely on multiple data sources) to execute queries from other contracts. Decentralization at the source and node-operator level is crucial—a network of oracle nodes serving information retrieved from the same source will run into the same problem as a centralized oracle.

It is also possible for stake-based oracles to slash node operators who fail to respond quickly to data requests. This significantly incentivizes oracle nodes to invest in fault-tolerant infrastructure and provide data in timely fashion.

Good incentive compatibility

Decentralized oracles implement various incentive designs to prevent Byzantine(opens in a new tab) behavior among oracle nodes. Specifically, they achieve attributability and accountability:

Decentralized oracle nodes are often required to sign the data they provide in response to data requests. This information helps with evaluating the historical performance of oracle nodes, such that users can filter out unreliable oracle nodes when making data requests. An example is Witnet’s Algorithmic Reputation System(opens in a new tab).
Decentralized oracles—as explained earlier—may require nodes to place a stake on their confidence in the truth of data they submit. If the claim checks out, this stake can be returned along with rewards for honest service. But it can also be slashed in case the information is incorrect, which provides some measure of accountability.
APPLICATIONS OF ORACLES IN SMART CONTRACTS

The following are common use-cases for oracles in Ethereum:

Retrieving financial data

Decentralized finance (DeFi) applications allow for peer-to-peer lending, borrowing, and trading of assets. This often requires getting different financial information, including exchange rate data (for calculating the fiat value of cryptocurrencies or comparing token prices) and capital markets data (for calculating the value of tokenized assets, such as gold or the US dollar).

A DeFi lending protocol, for example, needs to query current market prices for assets (e.g., ETH) deposited as collateral. This lets the contract determine the value of collateral assets and determine how much it can borrow from the system.

Popular “price oracles” (as they are often called) in DeFi include Chainlink Price Feeds, Compound Protocol’s Open Price Feed(opens in a new tab), Uniswap’s Time-Weighted Average Prices (TWAPs)(opens in a new tab), and Maker Oracles(opens in a new tab).

Builders should understand the caveats that come with these price oracles before integrating them into their project. This article(opens in a new tab) provides a detailed analysis of what to consider when planning to use any of the price oracles mentioned.

Below is an example of how you can retrieve the latest ETH price in your smart contract using a Chainlink price feed:

pragma solidity ^0.6.7;
import "@chainlink/contracts/src/v0.6/interfaces/AggregatorV3Interface.sol";
contract PriceConsumerV3 {
AggregatorV3Interface internal priceFeed;
/**
* Network: Kovan
* Aggregator: ETH/USD
* Address: 0x9326BFA02ADD2366b30bacB125260Af641031331
*/
constructor() public {
priceFeed = AggregatorV3Interface(0x9326BFA02ADD2366b30bacB125260Af641031331);
}
/**
* Returns the latest price
*/
function getLatestPrice() public view returns (int) {
(
uint80 roundID,
int price,
uint startedAt,
uint timeStamp,
uint80 answeredInRound
) = priceFeed.latestRoundData();
return price;
}
}
Show all
📋 Copy
Generating verifiable randomness

Certain blockchain applications, such as blockchain-based games or lottery schemes, require a high level of unpredictability and randomness to work effectively. However, the deterministic execution of blockchains eliminates randomness.

The original approach was to use pseudorandom cryptographic functions, such as blockhash, but these could be manipulated by miners(opens in a new tab) solving the proof-of-work algorithm. Also, Ethereum’s switch to proof-of-stake means developers can no longer rely on blockhash for onchain randomness. The Beacon Chain’s RANDAO mechanism(opens in a new tab) provides an alternative source of randomness instead.

It is possible to generate the random value offchain and send it onchain, but doing so imposes high trust requirements on users. They must believe the value was truly generated via unpredictable mechanisms and wasn’t altered in transit.

Oracles designed for offchain computation solve this problem by securely generating random outcomes offchain that they broadcast onchain along with cryptographic proofs attesting to the unpredictability of the process. An example is Chainlink VRF(opens in a new tab) (Verifiable Random Function), which is a provably fair and tamper-proof random number generator (RNG) useful for building reliable smart contracts for applications that rely on unpredictable outcomes. Another example is API3 QRNG(opens in a new tab) that serves Quantum random number generation (QRNG) is a public method of Web3 RNG based on quantum phenomena, served with the courtesy of the Australian National University (ANU).

Getting outcomes for events

With oracles, creating smart contracts that respond to real-world events is easy. Oracle services make this possible by allowing contracts to connect to external APIs through offchain components and consume information from those data sources. For example, the prediction dapp mentioned earlier may request an oracle to return election results from a trusted offchain source (e.g., the Associated Press).

Using oracles to retrieve data based on real-world outcomes enables other novel use cases; for example, a decentralized insurance product needs accurate information about weather, disasters, etc. to work effectively.

Automating smart contracts

Smart contracts do not run automatically; rather, an externally owned account (EOA), or another contract account, must trigger the right functions to execute the contract’s code. In most cases, the bulk of the contract’s functions are public and can be invoked by EOAs and other contracts.

But there are also private functions within a contract that are inaccessible to others;, but that are critical to a dapp's overall functionality. Examples include a mintERC721Token() function that periodically mints new NFTs for users, a function for awarding payouts in a prediction market, or a function for unlocking staked tokens in a DEX.

Developers will need to trigger such functions at intervals to keep the application running smoothly. However, this might lead to more hours lost on mundane tasks for developers, which is why automating execution of smart contracts is attractive.

Some decentralized oracle networks offer automation services, which allow offchain oracle nodes to trigger smart contract functions according to parameters defined by the user. Typically, this requires “registering” the target contract with the oracle service, providing funds to pay the oracle operator, and specifying the conditions or times to trigger the contract.

Chainlink’s Keeper Network(opens in a new tab) provides options for smart contracts to outsource regular maintenance tasks in a trust minimized and decentralized manner. Read the official Keeper's documentation(opens in a new tab) for information on making your contract Keeper-compatible and using the Upkeep service.

HOW TO USE BLOCKCHAIN ORACLES

There are multiple oracle applications you can integrate into your Ethereum dapp:

Chainlink(opens in a new tab) - Chainlink decentralized oracle networks provide tamper-proof inputs, outputs, and computations to support advanced smart contracts on any blockchain.

RedStone Oracles(opens in a new tab) - RedStone is a decentralized modular oracle that provides gas-optimized data feeds. It specializes in offering price feeds for emerging assets, such as liquid staking tokens (LSTs), liquid restaking tokens (LRTs), and Bitcoin staking derivatives.

Chronicle(opens in a new tab) - Chronicle overcomes the current limitations of transferring data onchain by developing truly scalable, cost-efficient, decentralized, and verifiable oracles.

Witnet(opens in a new tab) - Witnet is a permissionless, decentralized, and censorship-resistant oracle helping smart contracts to react to real world events with strong crypto-economic guarantees.

UMA Oracle(opens in a new tab) - UMA's optimistic oracle allows smart contracts to quickly and receive any kind of data for different applications, including insurance, financial derivatives, and prediction markets.

Tellor(opens in a new tab) - Tellor is a transparent and permissionless oracle protocol for your smart contract to easily get any data whenever it needs it.

Band Protocol(opens in a new tab) - Band Protocol is a cross-chain data oracle platform that aggregates and connects real-world data and APIs to smart contracts.

Paralink(opens in a new tab) - Paralink provides an open source and decentralized oracle platform for smart contracts running on Ethereum and other popular blockchains.

Pyth Network(opens in a new tab) - The Pyth network is a first-party financial oracle network designed to publish continuous real-world data onchain in a tamper-resistant, decentralized, and self-sustainable environment.

API3 DAO(opens in a new tab) - API3 DAO is delivering first-party oracle solutions that deliver greater source transparency, security and scalability in a decentralized solution for smart contracts

Supra(opens in a new tab) - A vertically integrated toolkit of cross-chain solutions that interlink all blockchains, public (L1s and L2s) or private (enterprises), providing decentralized oracle price feeds that can be used for onchain and offchain use-cases.

FURTHER READING

Articles

What Is a Blockchain Oracle?(opens in a new tab) — Chainlink
What is a Blockchain Oracle?(opens in a new tab) — Patrick Collins
Decentralised Oracles: a comprehensive overview(opens in a new tab) — Julien Thevenard
Implementing a Blockchain Oracle on Ethereum(opens in a new tab) – Pedro Costa
Why can't smart contracts make API calls?(opens in a new tab) — StackExchange
Why we need decentralized oracles(opens in a new tab) — Bankless
So you want to use a price oracle(opens in a new tab) — samczsun
Videos

Oracles and the Expansion of Blockchain Utility(opens in a new tab) — Real Vision Finance
The differences between first party and third party oracles(opens in a new tab) - Blockchain Oracle Summit
Tutorials

How to Fetch the Current Price of Ethereum in Solidity(opens in a new tab) — Chainlink
Consuming Oracle Data(opens in a new tab) — Chronicle
Example projects

Full Chainlink starter project for Ethereum in Solidity(opens in a new tab) — HackBG

-- https://ethereum.org/en/developers/docs/oracles/

