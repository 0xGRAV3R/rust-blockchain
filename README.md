# rust-blockchain

Simple example for building a blockchain in Rust

Start using

```bash
RUST_LOG=info cargo run
```

We’re using libp2p as our peer-to-peer networking layer and Tokio as our underlying runtime.

Our App struct essentially holds our application state. We won’t persist the blockchain in this example, so it will go away once we stop the application.

This state is simply a list of Blocks. We will add new blocks to the end of this list and this will actually be our blockchain data structure.

This starts the client locally. The blockchain is not persisted anywhere.

You can start it in multiple terminals to get multiple connected peer-to-peer clients.

In each client, you can enter the following commands:

* `ls p` - list peers
* `ls c` - print local chain
* `create b $data` - `$data` is just a string here - this creates (mines) a new block with the data entry `$data` and broadcasts it

Once a block is created by a node, it's broadcasted and the blockchain in all other nodes is updated (if it's a valid block).

On startup, a node asks another node on the network for their blockchain and, if it's valid and longer than the current local blockchain, it updates it's own chain to the longest one it receives.


This is a VERY overly simplified, offline-running, highly inefficient and insecure blockchain implementation. If a node gets out of sync, it's broken. This is an example for showing some of the concepts behind building a blockchain system in Rust, so it shouldn't be used anywhere near a production scenario, but you can have fun with it and learn something. :)
