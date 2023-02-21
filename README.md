# private-ethereum-playground

Reference: <https://geth.ethereum.org/docs/fundamentals/private-network#end-to-end-example>

Generally, by following the steps in the example a private Ethereum network can be created. Points to note:

1. When creating the new nodes, remember to store the password inside file `password.txt` and store them in the node directory for later usage.
2. For the `genesis.json` file, followings should be noted:
    1. Remember to update the value of `extradata` field as it specifies the signer addresses for the Clique Consensus Protocol.
    2. For the initial alloc, values should be much larger than the example. Or else the error `gas required exceeds allowance (0)` will be experienced (Those accounts do not have enough ether for the transaction...)
3. To start the two nodes, use the following commands (also update the `--unlock` addresses):
    `geth --datadir node1 --port 30306 --bootnodes enode://f7aba85ba369923bffd3438b4c8fde6b1f02b1c23ea0aac825ed7eac38e6230e5cadcf868e73b0e28710f4c9f685ca71a86a4911461637ae9ab2bd852939b77f@127.0.0.1:0?discport=30305  --networkid 12345 --unlock 0xC1B2c0dFD381e6aC08f34816172d6343Decbb12b --password node1/password.txt --authrpc.port 8551`

    `geth --datadir node2 --port 30307 --bootnodes enode://f7aba85ba369923bffd3438b4c8fde6b1f02b1c23ea0aac825ed7eac38e6230e5cadcf868e73b0e28710f4c9f685ca71a86a4911461637ae9ab2bd852939b77f@127.0.0.1:0?discport=30305  --networkid 12345 --unlock 0xC1B2c0dFD381e6aC08f34816172d6343Decbb12b --password node1/password.txt --authrpc.port 8552`

4. The following commands inside the JS console need to be run such that the blocks will can be mined and confirmed:
`miner.start()`
