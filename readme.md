# stdrpc

ES6+ compatible, isomorphic JSON-RPC module for node and the browser.

[![Build Status](https://travis-ci.org/montyanderson/stdrpc.svg?branch=master)](https://travis-ci.org/montyanderson/stdrpc)
[![Coverage Status](https://coveralls.io/repos/github/montyanderson/stdrpc/badge.svg?branch=master)](https://coveralls.io/github/montyanderson/stdrpc?branch=master)

* Compatible with [Bitcoin](https://bitcoin.org/), [Ethereum](https://www.ethereum.org/), [Zcash](https://z.cash/), and many more.
* Supports on-the-fly RPC methods using [Proxies](https://developer.mozilla.org/en/docs/Web/JavaScript/Reference/Global_Objects/Proxy)
* Works in browser and in node
* Very small codebase
* Uses [axios](https://github.com/mzabriskie/axios) behind the scenes

## Usage

``` javascript
const rpc = stdrpc({
	url: "http://localhost:8332"
});

rpc.getbalance().then(balance => {
	// woo!
});
```

## API

### stdrpc(options)

Returns a proxied object, returning a function for every method.

#### options

##### url

A `string` address of the RPC server.

##### username

A `string` username for authentication.

##### password

A `string` password authentication.

##### methodTransform

A `function` which all method names will be passed through.

``` javascript
// connecting to an ethereum node
const rpc = stdrpc("http://localhost:8545", {
	methodTransform: require("decamelize")
});

rpc.ethCoinbase() // becomes rpc.eth_coinbase()
```
