# Messari Standard Subgraphs &bull; [![GitHub license](https://img.shields.io/badge/license-MIT-blue)](https://github.com/messari/subgraphs/blob/master/LICENSE) [![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](docs/CONTRIBUTING.md) [![Issues Report](https://img.shields.io/badge/issues-report-yellow.svg)](https://github.com/messari/subgraphs/issues/new)

# NFTX Instructions

- Update the configuration.json to include the Non Fungible Position Manager and the Uniswap Factory Upgradable.

Also go into the /nftx-v3-goerli/configurations.ts and update the following sections with the new Uniswap Factory address.

```ts
  getFactoryAddress(): Bytes {
    return Bytes.fromHexString("0xaab56871c2f33fe49441d5a797bea1587555e8dc"); // shouldn't these be in the configuration.json?
  }
  getFactoryContract(): Factory {
    return Factory.bind(
      Address.fromString("0xaab56871c2f33fe49441d5a797bea1587555e8dc") // shouldn't these be in the configuration.json?
    );
  }
```

Also update the configurations.ts file and add the new Stable Oracle Pool

```ts
  getStableOraclePools(): Bytes[] {
    return stringToBytesList([
      "0x482cedc7b6f71af4370f4107444f0657a35e07ac", // NEW USDC/WETH POOL
      // 0xf8492c75a6c7477da43dbea5f3bf2dece0b23320 was the DAI/WETH pool used here before.
    ]);
  }
```

- Update the contract and blocks at `subgraphs/uniswap-v3-forks/protocols/nftx-v3/config/deployments/nftx-v3-goerli/configurations.ts` and run the following command `messari b nftx-v3-goerli -l -s hosted-service -d`
  Select `nftx-project` as the target to deploy to. Once it has been pushed you can check for liquidity pools by using the following https://thegraph.com/hosted-service/subgraph/nftx-project/nftx-v3-uniswap-goerli?playgroundQuery=135154

<p align="center">
  <a href="https://messari.io/protocol-explorer/all-protocols">
    <img src="./docs/images/messari-logo.png" alt="Messari Logo" width="460" />
  </a>
</p>

Messari subgraphs set an industry leading standard for on chain data 🚀

Utilizing [The Graph](https://thegraph.com/) these subgraphs extract raw blockchain data and transform it into meaningful metrics, for products and analytics.

We aim to make sense of DEFI protocols in an open, holistic approach capturing every piece of data from a given protocol type.

> Protocol types supported: [Lending](./schema-lending.graphql), [CDP](./schema-lending.graphql), [DEX](./schema-dex-amm.graphql), [Yield Aggregator](./schema-yield.graphql), [NFT Marketplace](./schema-nft-marketplace.graphql), [Network](./schema-network.graphql), [Bridge](./schema-bridge.graphql), [Perpetual Futures](./schema-derivatives-perpfutures.graphql), [Options](./schema-derivatives-options.graphql), Governance

<sub>If you are a protocol and want to collaborate please visit [messari.io/web3-data-collaboration](https://messari.io/web3-data-collaboration)</sub>

## Working Environment

Go to [`docs/SETUP.md`](./docs/SETUP.md) to learn how to setup your machine for Messari subgraph development.

## Learn the Project

It is important to familiarize yourself with the project structure and tooling to build efficiently. Go to [`docs/STRUCTURE.md`](./docs/STRUCTURE.md) and [`docs/TOOLING.md`](./docs/TOOLING.md) to learn more.

- Familiarize yourself with our schemas labeled `schema-{protocol type}.graphql`. Read more details in [`docs/SCHEMA.md`](./docs/SCHEMA.md)
- We update our schemas as necessary. You can find out about each upgrade in [`docs/CHANGES.md`](./docs/CHANGES.md)
- To learn about Messari standard methodologies see [`docs/METHODOLOGY.md`](./docs/METHODOLOGY.md)

## Becoming a Subgraph Developer

Becoming a good subgraph developer will take patience and practice. The following resources are for developers of all skill levels to learn the ins and outs of subgraph development. 👾

- For a full walkthrough of our subgraph development process visit [`docs/WALKTHROUGH.md`](./docs/WALKTHROUGH.md).
- Resources for development of varying levels can be found in [`docs/RESOURCES.md`](./docs/RESOURCES.md).
- To learn about common errors, best error handling practices, and debugging see [`docs/ERRORS.md`](./docs/ERRORS.md)
- Subgraph performance is also a concern. Learn about indexing / querying performance by reading [`docs/PERFORMANCE`](./docs/PERFORMANCE.md)
- Learn about retrieving prices in subgraphs and how to handle this in [`docs/ORACLES.md`](./docs/ORACLES.md)

## Contributing Guidelines

We welcome contributions from the community! You can point out or fix bugs, suggest changes, add new features, or add new subgraphs. ✅

- For bugs, features, or change requests please submit an [issue](https://github.com/messari/subgraphs/issues) following our [guide](./docs/ISSUES.md).
- General contribution guidelines and practices will be found in [`docs/CONTRIBUTING.md`](./docs/CONTRIBUTING.md)

## Development Status

You can find a visualizer with the status of all Messari subgraphs at [subgraphs.xyz](https://subgraphs.messari.io/)! The code lives under `./dashboard`.

You can see our subgraphs supporting the data for our product ["Protocol Metrics"](https://messari.io/protocol-explorer/all-protocols)

> _Quick note_: the raw deployment status of all subgraphs lives in [`./deployment/deployment.json`](./deployment/deployment.json)
