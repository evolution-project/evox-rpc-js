# EvoX RPC Daemon and RPC Wallet Javascript Library

Javascript library to interact with RPC Daemon and RPC Wallet.\
All requests are queued. Most functions are async.

Since version 0.2.0 the RPCDaemon and RPCWallet objects are created using a factory function instead of declaring the object with "new".

There is no need to connect and disconnect the underlying socket anymore.

The library supports HTTP, HTTPS and digest authentication.

The library use an axios interceptor to implement digest authentication.

Digest authentication is activated as soon as a username and a password is supplied during object creation.

Once initialized simply use the query functions.


## RPCDaemon without Digest Authentication

```javascript
const rpcDaemon = require('@evox/evox-rpc').RPCDaemon

const daemonClient = rpcDaemon.createDaemonClient({
  url: 'http://127.0.0.1:52521'
})
// When using a self signed certificate with HTTPS you need to set the function sslRejectUnauthorized to false.
daemonClient.sslRejectUnauthorized(false)
```


## RPCDaemon with Digest Authentication

```javascript
const rpcDaemon = require('@evox/evox-rpc').RPCDaemon

const daemonClient = rpcDaemon.createDaemonClient({
  url: 'http://127.0.0.1:52521',
  username: 'user',
  password: 'pass'
})
// When using a self signed certificate with HTTPS you need to set the function sslRejectUnauthorized to false.
daemonClient.sslRejectUnauthorized(false)
```


## RPCWallet without Digest Authentication

```javascript
const rpcWallet = require('@evox/evox-rpc').RPCWallet

const walletClient = rpcWallet.createWalletClient({
  url: 'http://127.0.0.1:52528'
})
// When using a self signed certificate with HTTPS you need to set the function sslRejectUnauthorized to false.
walletClient.sslRejectUnauthorized(false)
```


## RPCWallet with Digest Authentication

```javascript
  const rpcWallet = require('@evox/evox-rpc').RPCWallet

  const walletClient = rpcWallet.createWalletClient({
  url: 'http://127.0.0.1:52528',
  username: 'user',
  password: 'pass'
})
// When using a self signed certificate with HTTPS you need to set the function sslRejectUnauthorized to false.
walletClient.sslRejectUnauthorized(false)
```

## Generate JSDoc documentation
```
npm run generate-docs
```

## Get unit tests list
```
npm test
```

## MarketPlace Tests
***NOTE: tests can take several minutes to complete while block confirmations occur***
1. Use Console to restore a testnet wallet from seed
```
./simplewallet --restore-wallet cosmos.test --password 123456 
```
2. Use Console to execute following command to open normal wallet as a service with screen
```
screen -S regularwallet ./simplewallet --wallet-file cosmos.test --password 123456 --rpc-bind-ip 0.0.0.0 --rpc-bind-port 52528 --daemon-address 0.0.0.0:52521
```
3. Run the market-place tests
```
npm run test-wallet-market-place
```

## Wallet Tests
1. Use Console to restore a testnet wallet from seed
```
./simplewallet --restore-wallet cosmos.test --password 123456 
```
2. Use Console to execute following command to open normal wallet as a service with screen
```
screen -S regularwallet ./simplewallet --wallet-file cosmos.test --password 123456 --rpc-bind-ip 0.0.0.0 --rpc-bind-port 52528 --daemon-address 0.0.0.0:52521
```
3. Run the wallet tests
```
npm run test-wallet-account
```

## Atomics Tests
***NOTE: tests require two wallets and can take several minutes to complete while block confirmations occur***
1. Use Console to restore a testnet wallet from seed
```
./simplewallet --restore-wallet cosmos.test --password 123456 
```
2. when instructed, provide the following seed phrase
```
coffee rest stand said leg muse defense wild about mighty horse melt really hum sharp seek honest brush depress beyond hundred silly confusion inhale birthday frozen
```
3. when instructed, provide the following password for the secured seed
```
123456
```
4. Use Console to execute following command to open normal wallet as a service with screen
```
screen -S regularwallet ./simplewallet --wallet-file cosmos.test --password 123456 --rpc-bind-ip 0.0.0.0 --rpc-bind-port 52528 --daemon-address 0.0.0.0:52521
```
5. Use Console to restore a testnet wallet from seed
```
./simplewallet --restore-wallet cosmos.test --password 123456 
```
6. when instructed, provide the following seed phrase
```
obviously essence rise wow appear glove veil gain beneath ask suddenly manage thunder near sympathy respect pants led lucky pie rant water deeply mean shift somebody
```
7. when instructed, provide the following password for the secured seed
```
123456
```
8. Use Console to execute following command to open normal wallet as a service with screen
```
screen -S otherwallet ./simplewallet --wallet-file cosmos.other --password 123456 --rpc-bind-ip 0.0.0.0 --rpc-bind-port 12234 --daemon-address 0.0.0.0:52521
```
9. Run the atomic tests
```
npm run test-wallet-atomics
```

## Cold Signing Tests
1. Use Console to restore a testnet wallet from seed
```
./simplewallet --restore-wallet cosmos.test --password 123456 
```
2. when instructed, provide the following seed phrase
```
coffee rest stand said leg muse defense wild about mighty horse melt really hum sharp seek honest brush depress beyond hundred silly confusion inhale birthday frozen
```
3. when instructed, provide the following password for the secured seed
```
123456
```
4. Use Simplewallet console execute the following to save a watch_only wallet
```
save_watch_only cosmos.watch 123456
```
5. Use Console to execute following command to open watch_only wallet as a service with screen
```
screen -S watchonlywallet ./simplewallet --wallet-file cosmos.watch --password 123456 --rpc-bind-ip 0.0.0.0 --rpc-bind-port 12234 --daemon-address 0.0.0.0:52521
```
6. Use Console to execute following command to open normal wallet as a service with screen
```
screen -S regularwallet ./simplewallet --wallet-file cosmos.test --password 123456 --rpc-bind-ip 0.0.0.0 --rpc-bind-port 52528 --daemon-address 0.0.0.0:52521
```
7. Run the cold-signing tests
```
npm run test-wallet-cold-signing
```

## Contract Tests
***NOTE: tests require two wallets and can take several minutes to complete while block confirmations occur***
1. Use Console to restore a testnet wallet from seed
```
./simplewallet --restore-wallet cosmos.test --password 123456 
```
2. when instructed, provide the following seed phrase
```
coffee rest stand said leg muse defense wild about mighty horse melt really hum sharp seek honest brush depress beyond hundred silly confusion inhale birthday frozen
```
3. when instructed, provide the following password for the secured seed
```
123456
```
4. Use Console to execute following command to open normal wallet as a service with screen
```
screen -S regularwallet ./simplewallet --wallet-file cosmos.test --password 123456 --rpc-bind-ip 0.0.0.0 --rpc-bind-port 52528 --daemon-address 0.0.0.0:52521
```
5. Use Console to restore a testnet wallet from seed
```
./simplewallet --restore-wallet cosmos.test --password 123456 
```
6. when instructed, provide the following seed phrase
```
obviously essence rise wow appear glove veil gain beneath ask suddenly manage thunder near sympathy respect pants led lucky pie rant water deeply mean shift somebody
```
7. when instructed, provide the following password for the secured seed
```
123456
```
8. Use Console to execute following command to open normal wallet as a service with screen
```
screen -S otherwallet ./simplewallet --wallet-file cosmos.other --password 123456 --rpc-bind-ip 0.0.0.0 --rpc-bind-port 12234 --daemon-address 0.0.0.0:52521
```
9. Run the contract tests
```
npm run test-wallet-contracts
```