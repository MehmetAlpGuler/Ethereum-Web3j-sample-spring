Microsoft Windows [Version 10.0.18362.418]
(c) 2019 Microsoft Corporation. All rights reserved.

Open Command Prompt
C:\Users\MehmetAlpGuler>docker run -d --name ethereum -p 8545:8545 -p 30303:30303 ethereum/client-go --rpc --rpcaddr "0.0.0.0" --rpcapi="db,eth,net,web3,personal" --rpccorsdomain "*" --dev
Unable to find image 'ethereum/client-go:latest' locally
latest: Pulling from ethereum/client-go
89d9c30c1d48: Pull complete                                                                                             3ec15e1c64e1: Pull complete                                                                                             7e7e9231cd83: Pull complete                                                                                             Digest: sha256:246adf54ec57aae79dbafcc23c8269984e37c7973a6f732342926c4b2d941191
Status: Downloaded newer image for ethereum/client-go:latest
c0e1333e294a7e07113e2af52fc2257f1e0095d47133d8d297c8df8b6b6bd5e5

C:\Users\MehmetAlpGuler>docker exec -it ethereum geth attach ipc:/tmp/geth.ipc
Welcome to the Geth JavaScript console!

instance: Geth/v1.9.7-unstable-db79143a-20191024/linux-amd64/go1.13.3
coinbase: 0xc2b158964533a3e746bdd743f7fd6745d28fdc3a
at block: 0 (Thu, 01 Jan 1970 00:00:00 UTC)
 datadir:
 modules: admin:1.0 clique:1.0 debug:1.0 eth:1.0 miner:1.0 net:1.0 personal:1.0 rpc:1.0 shh:1.0 txpool:1.0 web3:1.0

> eth.coinbase
"0xc2b158964533a3e746bdd743f7fd6745d28fdc3a"
> eth.accounts
["0xc2b158964533a3e746bdd743f7fd6745d28fdc3a"]
> eth.getBalance(eth.accounts[0])
1.15792089237316195423570985008687907853269984665640564039457584007913129639927e+77
> personal.newAccount("123456")
>                                                                                                                                                              newAccount("123456")
"0xe43d72a3fc3c8f8d104e54468b26b903ad90ae9a"
> personal.newAccount("123456")
"0x1668513e16fa30e7dcafe61c3f9a155b68ad764e"
> eth.accounts
["0xc2b158964533a3e746bdd743f7fd6745d28fdc3a", "0xb5205157a528e6cb8d02cf92cb53321c75d6f9ce", "0xe43d72a3fc3c8f8d104e54468b26b903ad90ae9a", "0x1668513e16fa30e7dcafe61c3f9a155b68ad764e"]
> eth.sendTransaction({from: eth.coinbase, to: eth.accounts[1], value: 1000})
"0xc28e6f14255636efd9dd98bdeb6b501d3da3e434e3036892c3e74cb94bda892d"
> eth.sendTransaction({from: eth.coinbase, to: eth.accounts[2], value: 2000})
"0xc1f3ac7ca253f4e2521caf517cdf3d8810a1044aa44969645b8d840baa6dc3a3"
> eth.getBalance(eth.accounts[1])
1000
>


Test With App
 curl --header "Content-Type: application/json" --request POST --data  "{ """fromId""":2, """toId""":1, """value""":3 }" http://localhost:8090/transaction