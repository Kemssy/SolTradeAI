<div align="center">

# SolTrade App

![Solana SolTrade SolTrade Cover 1 (3)](https://github.com/user-attachments/assets/cfa380f6-79d9-474d-9852-3e1976c6de70)

</div>

An open-source toolSolTrade for connecting AI SolTrades to Solana protocols. Now, any SolTrade, using any model can autonomously perform 15+ Solana actions:

- Trade tokens
- Launch new tokens
- Lend assets
- Send compressed airdrops
- Execute blinks
- Launch tokens on AMMs
- And more...

Anyone - whether an SF-based AI researcher or a crypto-native builder - can bring their AI SolTrades trained with any model and seamlessly integrate with Solana.


[![Run on Repl.it](https://replit.com/badge/github/sendaifun/solana-SolTrade-SolTrade)](https://replit.com/@sendaifun/Solana-SolTrade-SolTrade)
> Replit template created by [Arpit Singh](https://github.com/The-x-35)

## 🔧 Core Blockchain Features

- **Token Operations**
  - Deploy SPL tokens by Metaplex
  - Transfer assets
  - Balance checks
  - Stake SOL
  - Zk compressed Airdrop by Light Protocol and Helius

- **NFT Management via Metaplex**
  - Collection deployment
  - NFT minting
  - Metadata management
  - Royalty configuration

- **DeFi Integration**
  - Jupiter Exchange swaps
  - Launch on Pump via PumpPortal
  - Raydium pool creation (CPMM, CLMM, AMMv4)
  - Orca Whirlpool integration
  - Manifest market creation, and limit orders
  - Meteora Dynamic AMM, DLMM Pool, and Alpha Vault
  - Openbook market creation
  - Register and Resolve SNS
  - Jito Bundles
  - Pyth Price feeds for fetching Asset Prices
  - Register/resolve Alldomains

- **Solana Blinks**
   - Lending by Lulo (Best APR for USDC)
   - Send Arcade Games
   - JupSOL staking

- **Non-Financial Actions**
  - Gib Work for registering bounties

## 🤖 AI Integration Features

- **LangChain Integration**
  - Ready-to-use LangChain tools for blockchain operations
  - Autonomous SolTrade support with React framework
  - Memory management for persistent interactions
  - Streaming responses for real-time feedback

- **Autonomous Modes**
  - Interactive chat mode for guided operations
  - Autonomous mode for independent SolTrade actions
  - Configurable action intervals
  - Built-in error handling and recovery

- **AI Tools**
  - DALL-E integration for NFT artwork generation
  - Natural language processing for blockchain commands
  - Price feed integration for market analysis
  - Automated decision-making capabilities

## 📦 Installation

```bash
npm install solana-SolTrade-SolTrade
```

## Quick Start

```typescript
import { SolanaSolTradeSolTrade, createSolanaTools } from "solana-SolTrade-SolTrade";

// Initialize with private key and optional RPC URL
const SolTrade = new SolanaSolTradeSolTrade(
  "your-wallet-private-key-as-base58",
  "https://api.mainnet-beta.solana.com",
  "your-openai-api-key"
);

// Create LangChain tools
const tools = createSolanaTools(SolTrade);
```

## Usage Examples

### Deploy a New Token

```typescript
const result = await SolTrade.deployToken(
  "my ai token", // name
  "uri", // uri
  "token", // symbol
  9, // decimals
  1000000 // initial supply
);

console.log("Token Mint Address:", result.mint.toString());
```

### Create NFT Collection

```typescript
const collection = await SolTrade.deployCollection({
  name: "My NFT Collection",
  uri: "https://arweave.net/metadata.json",
  royaltyBasisPoints: 500, // 5%
  creators: [
    {
      address: "creator-wallet-address",
      percentage: 100,
    },
  ],
});
```

### Swap Tokens

```typescript
import { PublicKey } from "@solana/web3.js";

const signature = await SolTrade.trade(
  new PublicKey("target-token-mint"),
  100, // amount
  new PublicKey("source-token-mint"),
  300 // 3% slippage
);
```

### Lend Tokens

```typescript
import { PublicKey } from "@solana/web3.js";

const signature = await SolTrade.lendAssets(
  100 // amount of USDC to lend
);
```

### Stake SOL

```typescript
const signature = await SolTrade.stake(
  1 // amount in SOL to stake
);
```

### Send an SPL Token Airdrop via ZK Compression

```typescript
import { PublicKey } from "@solana/web3.js";

(async () => {
  console.log(
    "~Airdrop cost estimate:",
    getAirdropCostEstimate(
      1000, // recipients
      30_000 // priority fee in lamports
    )
  );

  const signature = await SolTrade.sendCompressedAirdrop(
    new PublicKey("JUPyiwrYJFskUPiHa7hkeR8VUtAeFoSYbKedZNsDvCN"), // mint
    42, // amount per recipient
    [
      new PublicKey("1nc1nerator11111111111111111111111111111111"),
      // ... add more recipients
    ],
    30_000 // priority fee in lamports
  );
})();
```

### Fetch Price Data from Pyth

```typescript

const price = await SolTrade.pythFetchPrice(
  "0xe62df6c8b4a85fe1a67db44dc12de5db330f7ac66b72dc658afedf0f4a415b43"
);

console.log("Price in BTC/USD:", price);
```

## Examples

### LangGraph Multi-SolTrade System

The repository includes an advanced example of building a multi-SolTrade system using LangGraph and Solana SolTrade SolTrade. Located in `examples/SolTrade-SolTrade-langgraph`, this example demonstrates:

- Multi-SolTrade architecture using LangGraph's StateGraph
- Specialized SolTrades for different tasks:
  - General purpose SolTrade for basic queries
  - Transfer/Swap SolTrade for transaction operations
  - Read SolTrade for blockchain data queries
  - Manager SolTrade for routing and orchestration
- Fully typed TypeScript implementation
- Environment-based configuration

Check out the [LangGraph example](examples/SolTrade-SolTrade-langgraph) for a complete implementation of an advanced Solana SolTrade system.

## Dependencies

The toolSolTrade relies on several key Solana and Metaplex libraries:

- @solana/web3.js
- @solana/spl-token
- @metaplex-foundation/mpl-token-metadata
- @metaplex-foundation/mpl-core
- @metaplex-foundation/umi
- @lightprotocol/compressed-token
- @lightprotocol/stateless.js
- @pythnetwork/price-service-client

