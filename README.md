# Solana-Signal-Engine
Read-only Solana token monitoring and on-chain intelligence system built with TypeScript, Node.js and SQLite.
A local-first, read-only Solana collector and analysis foundation for memecoin risk alerts. The project currently implements scope and configuration, focused launch discovery, token security checks, liquidity analysis, holder distribution, and bounded developer-wallet intelligence (Phases 1–7). It does not trade, sign transactions, hold keys, or custody funds.

Run locally
Use Node.js 22 or newer.

npm ci
cp .env.example .env
npm run build
npm test
npm run collect
Edit .env for local paths or RPC overrides. It is ignored by Git. Keep credentials out of the checked-in JSON configuration, and never add private keys or seed phrases: this bot has no signing path.

The collector uses free public Solana RPC endpoints by default and limits itself to four requests per second. Global discovery is focused on Pump.fun launches. PumpSwap and Raydium activity is followed only for discovered tokens and their associated addresses. Capacity limits refuse excess notices visibly and record coverage metrics; collection is not comprehensive. The current liquidity analyzer supports PumpSwap constant-product pools and Raydium AMM v4, with unknown results where ownership, reserves, pricing, or custody cannot be proven.

See scope, collector design, token security, liquidity analysis, holder distribution, and developer intelligence for the exact boundaries and evidence rules.


Solana RPC
    ↓
Token Discovery
    ↓
On-chain Collectors
    ↓
┌───────────────────────────┐
│ Security Analysis         │
│ Liquidity Analysis        │
│ Holder Analysis           │
│ Developer Intelligence    │
│ Early Transaction Analysis│
│ Bundle Detection          │
└───────────────────────────┘
    ↓
Signal / Risk Engine
    ↓
SQLite
    ↓
Telegram Alerts
