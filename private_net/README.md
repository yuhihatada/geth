# gethの使い方

## Gethの初期化

macOS
```
$ geth --datadir ~/yuhi-workspace/geth/private_net/ init ~/yuhi-workspace/geth/private_net/genesis.json
```

## Gethの起動

macOS
```
$ geth --networkid "10" --nodiscover --datadir ~/yuhi-workspace/geth/private_net --http --http.addr "localhost" --http.port "8545" --http.corsdomain "*" --http.api "eth,net,web3,personal" --miner.gaslimit "20000000" --allow-insecure-unlock console 2>> ~/yuhi-workspace/geth/private_net/error.log
```

## password解除しながら起動

macOS
```
$ geth --networkid "10" --nodiscover --datadir ~/yuhi-workspace/geth/private_net --http --http.addr "localhost" --http.port "8545" --http.corsdomain "*" --http.api "eth,net,web3,personal" --miner.gaslimit "20000000" --allow-insecure-unlock console 2>> ~/yuhi-workspace/geth/private_net/error.log --unlock 0xb47f08cc7ddc9aa27b3bbd45e42ee8825dc2ecf5,0xb4941002b9a012ff17186a3c1db72f423b615626,0xc1e1b83a482480e9e3cce55003cad6f4fac7b7c4 --password ~/yuhi-workspace/geth/private_net/password.txt
```

## Gethの終了

```
$ exit
```

## アカウント

### アカウント作成

```
$ personal.newAccount("pass")
```

#### アカウント一覧確認

```
$ eth.accounts
```

#### 指定アカウント確認

```
$ eth.accounts[n]
```

### コインベースアカウントの確認

```
$ eth.coinbase
```

### コインベースアカウントの変更

```
$ miner.setEtherbase(eth.accounts[n])
```

### コインベースの残高確認

wei
```
$ eth.getBalance(eth.accounts[0])
```

ether
```
$ web3.fromWei(eth.getBalance(eth.accounts[0]), "ether")
```

### ロックの解除

```
$ personal.unlockAccount(eth.accounts[0])
```

## マイニング

### マイニングの開始

```
$ miner.start(1)
```

### マイニングの停止

```
$ miner.stop()
```

### マイニング実行中かの確認

```
$ eth.mining
```

-> true: マイニング中  
-> false: マイニング停止  

## 単位変換

weiからetherへ
```
web3.fromWei(<wei単位>, "ether")
```

etherからweiへ
```
web3.toWei(<ether単位>, "ether")
```

## 送金

### トランザクションの発行

etherの送金
```
$ eth.sendTransaction({from: eth.accounts[0], to: eth.accounts[2], value:web3.toWei(5, "ether")})
```

-> トランザクションが発行される。この時点では送金が完了していない。  

## トランザクションの確認

```
$ 
```


## genesisブロックの確認

```
$ eth.getBlock(n)
```

## genesis.json

Genesisブロック作成の準備はgenesis.jsonに記載する。  