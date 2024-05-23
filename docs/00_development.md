# Development Docs

`SCAMMSwap`, means Smart Contract Automatic Market Maker Swap, nothing related to rugpulls, don't even try it kiddo..

We are going to build two apps: 
1. On chain one, Smart Contract based 
2. Off chain one, based in Smart Contracts

## On chain one, Smart Contract based, in a nutshell:
An account in ethereum contains the following data
- Balance
- Code (bytecode from the SC)
- Storage (immutable state from the SC)
- Nonce (A serial integer, used to prevent replay attacks)

Here we can trigger SC functions from the bytecode, and excecute it from the EVM
Users can interact with SC, through transactions:
    - Encoded contract function name
    - Function parameters

Transactions are "packed" in blocks, and mined/minted/validated into the blockchain.
SC are similar to JSON APIs, but instead of endpoints you can call smart contracct functions and provide function arguments, simillar to API backends. Unlike JSON API, to transitionate a state we need to send a transaction to mutate the blockchain state, and pay for each transaction.

In modern era the EVM execution layer and the consensus mechanism are decoupled into modules, and we are looking for client diversity as well language diversity to avoid a single point of failure.

Ethereum will expose a JSON-RPC API, and through this API we can interact with a node:
- Get Account data
    - balance, code, storage, nonce
- Get Block data
    - Block number, hash, parent hash, timestamp, difficulty, gas limit, gas used, transactions, uncles
- Get Transaction data
    - from, to, value, 
    - gas: gas, gas price
    - ECDSA data: v, r, s
    - Nonce, block hash, block number, etc

- a transaction will be sent using the ethereum JSON-RPC API: `eth_sendTransaction`
//CREATE A POST REQUEST TO SEND A TRANSACTION TO THE NETWORK


```json
    JSON='{
        "jsonrpc":"2.0",
        "method":"eth_sendTransaction",
        "params":[{
            "from": "vitalik.eth", 
            "to": "0x0000000000000000000000000000000000000000", 
            "value": "0x1000000000000000000000000000000000000000"
        }],
        "id":1
    }'      
```

```sh
    #vitalik burning eth
    curl -X POST
        -H "Content-Type: application/json"
        --data $JSON
        http://localhost:8545                 
```

## Tech stack for SCAMMSwap:
# On-chain development:
- Foundry ( Forge for Solidity, Anvil Node, Cast CLI, Chisel a Solidity REPL  )
- Solidity
- Rust ether.rs (`@TBD maybe expected`)

# Off-chain Frontend development:
- Ethers.js ( For solidity integration )
- nextJS, React + wagmi + viem ( For the frontend spaghetti )
- Vercel ( For hosting )
- Github Actions, for CI/CD
- React Native, expo ( for mobile app, `@TBD maybe expected` )
- Sentry ( for monitoring, coverage, and performance issues `@TBD maybe expected` )

# Off-chain features SCAMMASwap API, nice to have, for real practice.
- `RUST ethers.rs, @TBD maybe expected, not even necessary`
- `GOLANG go-ethereum, @TBD maybe expected, not even necessary`
- `TS ethers, @TBD maybe expected, not even necessary`
- Routes, Pool, Swap, Liquidity, etc



