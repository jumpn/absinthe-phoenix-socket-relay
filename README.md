# @jumpn/absinthe-phoenix-socket-relay

> Absinthe Phoenix Socket Relay

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
<!-- END doctoc -->

- [Installation](#installation)
  - [Using npm](#using-npm)
  - [Using yarn](#using-yarn)
- [Example](#example)
  - [relay-environment.js](#relay-environmentjs)
- [API](#api)
  - [createFetcher](#createfetcher)
  - [createSubscriber](#createsubscriber)
  - [isSubscribed](#issubscribed)
- [References](#references)
- [License](#license)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Installation

### Using [npm](https://docs.npmjs.com/cli/npm)

    $ npm install --save @jumpn/absinthe-phoenix-socket-relay

### Using [yarn](https://yarnpkg.com)

    $ yarn add @jumpn/absinthe-phoenix-socket-relay

## Example

### relay-environment.js

```javascript
// @flow

import {Environment, Network} from "relay-runtime";

import {createFetcher, createSubscriber} from "@absinthe-phoenix-socket-relay";

import absintheSocket from "./absintheSocket";

export default new Environment({
  network: Network.create(
    createFetcher(absintheSocket),
    createSubscriber(absintheSocket)
  ),
  store: new Store(new RecordSource())
});
```

## API

<!-- Generated by documentation.js. Update this documentation by updating the source code. -->

### createFetcher

Creates a Fetcher (Relay FetchFunction) using the given AbsintheSocket
instance

**Parameters**

-   `absintheSocket` **AbsintheSocket** 
-   `onError` **function (error: [Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)): any** 

Returns **FetchFunction** 

### createSubscriber

Creates a Subscriber (Relay SubscribeFunction) using the given AbsintheSocket
instance

**Parameters**

-   `absintheSocket` **AbsintheSocket** 
-   `onRecoverableError` **function (error: [Error](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Error)): any** 

Returns **SubscribeFunction** 

### isSubscribed

Returns a promise that resolves to `true` in case subscription of given
disposable has started or to `false` otherwise

**Parameters**

-   `disposable` **Disposable** 

Returns **[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)&lt;[boolean](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Boolean)>** 

## References

-   [Absinthe Phoenix Socket](https://github.com/jumpn/absinthe-phoenix-socket)
-   **Relay**
    -   [Environment](https://facebook.github.io/relay/docs/relay-environment.html)
    -   [NetworkLayer](https://facebook.github.io/relay/docs/network-layer.html)
    -   [FetchFunction](https://github.com/facebook/relay/blob/master/packages/relay-runtime/network/RelayNetworkTypes.js#L79)
    -   [SubscribeFunction](https://github.com/facebook/relay/blob/master/packages/relay-runtime/network/RelayNetworkTypes.js#L93)

## License

[MIT](LICENSE.txt) :copyright: **Jumpn Limited** / Mauro Titimoli (mauro@jumpn.com)
