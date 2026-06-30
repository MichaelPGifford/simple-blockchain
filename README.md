# simple-blockchain

A minimal blockchain implemented from scratch in Go — genesis block, SHA-256
block hashing, and hash-linked blocks. I built it to *understand the primitives*
before designing a real project on top of them.

> **Why this exists.** This was the first step of a two-part experiment. Before
> building a real-estate investment platform, I wanted to actually understand how
> a blockchain works at the byte level so I could make an informed call: roll my
> own chain, or issue tokens on an existing one? This repo is the "build one from
> scratch to learn" half. The conclusion — issue ERC-20 tokens on Ethereum rather
> than maintain a bespoke chain — became
> [`RealEstateToken`](https://github.com/MichaelPGifford/RealEstateToken).

## What it implements

- A `Block` with a timestamp, previous-block hash, data payload, and its own hash.
- `SetHash()` — SHA-256 over `prevHash || data || timestamp`.
- A `Blockchain` that starts from a genesis block and links each new block to the
  hash of the one before it.

## What it deliberately does *not* implement

So the takeaways are honest: there is **no proof-of-work** (no nonce/difficulty),
**no persistence**, **no networking/consensus**, and **no transaction model**.
It's a teaching skeleton of the data structure, not a functioning cryptocurrency.

## Run it

```bash
go run main.go
```

```
Blockchain in Go
Prev Hash:
Data: Genesis Block
Hash: <sha256>

Prev Hash: <sha256 of genesis>
Data: Send 1 BTC to User
Hash: <sha256>
...
```

## What it taught me

That a "blockchain" is, at its core, a hash-linked list — and that the genuinely
hard parts (consensus, proof-of-work, p2p networking, double-spend prevention) are
everything I left out here. Seeing that boundary clearly is exactly what let me
decide *not* to build my own chain for the next project, and to build on Ethereum
instead.

## License

MIT
