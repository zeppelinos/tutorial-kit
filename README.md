# Tutorial Kit
A ZeppelinOS kit containing React, ZeppelinOS, OpenZeppelin, Truffle and Infura.

This kit will guide you through deploying and upgrading your contracts using ZeppelinOS.

## Requirements

Install ZeppelinOS, Ganache, and Truffle

```
npm install -g truffle@5.0.2 ganache-cli@6.3.0 zos@2.3.0
```

## Installation

First ensure you are in a new and empty directory.

Run the `unpack` command.

```javascript
zos unpack tutorial
```

## Run

Run your local blockchain:

```
ganache-cli --secure -u 0 -u 1 -u 2 --deterministic
```

Initialize the ZeppelinOS project

```javascript
zos init tutorial
```

In the `client` directory, we run the React app.

```javascript
// in another terminal (i.e. not in the truffle develop prompt)
cd client
npm run start
```

## Test

Truffle can run tests written in Solidity or JavaScript against your smart contracts. Note the command varies slightly if you're in or outside of the development console.

```javascript
// inside the development console.
test

// outside the development console..
truffle test
```

Jest is included for testing React components. Compile your contracts before running Jest, or you may receive some file not found errors.

```javascript
// ensure you are inside the client directory when running this
npm run test
```

## Build

To build the application for production, use the build script. A production build will be in the `client/build` folder.

```javascript
// ensure you are inside the client directory when running this
npm run build
```

## FAQ

* __How do I use this with the Ganache-CLI?__

    It's as easy as modifying the config file! [Check out our documentation on adding network configurations](http://truffleframework.com/docs/advanced/configuration#networks). Depending on the port you're using, you'll also need to update line 29 of `client/src/utils/getWeb3.js`.

* __Where is my production build?__

    The production build will be in the `client/build` folder after running `npm run build` in the `client` folder.

* __Where can I find more documentation?__

    This kit is a marriage of [ZeppelinOS](https://zeppelinos.org//) and a React setup created with [create-react-app](https://github.com/facebookincubator/create-react-app/blob/master/packages/react-scripts/template/README.md). Either one would be a great place to start!

## Quick Command Reference

* Add a contract: `zos add <contract_name>`
* Create a session: `zos session --network <network_name> --from <default_address> --expires 36000`
* Compile all contract and deploy them: `zos push --deploy-dependencies`
* Create upgradeable instance of a contract: `zos create <contract_name>`
* Update an upgradeable contract: `zos update <contract_name>`
* Test contracts: `truffle test`
* Test dapp: `cd client && npm test`
* Run dev server: `cd client && npm run start`
* Build for production: `cd client && npm run build`