---
description: guide on how to install the js-mcs-sdk package and its basic usage
---

# Get Started

## Installation

Install the package using npm. It is recommended to create a new directory for a new project. Run the init command to setup a package.json file

```
npm init -y
npm install js-mcs-sdk
```

## Environment Variables

Set your API Key and Access Token as environment variables in a `.env` file. Optionally include your wallet's private key and RPC-URL.

```
API_KEY=<API_KEY>
ACCESS_TOKEN=<ACCESS_TOKEN>

# optional
PRIVATE_KEY=<PRIVATE_KEY>
RPC_URL=<RPC_URL>
```

{% hint style="info" %}
Be careful not to expose this information! \
Revealing your private key to others will give them access to your wallet.
{% endhint %}

## Writing SDK Scripts

To begin writing a script utilizing the SDK, create a new `.js` file.&#x20;

At the top of this file, require the necessary packages. Since these functions are [asynchronous](https://javascript.info/async-await), we will need to create an `async` function to run the SDK methods.

Now inside the asynchronous `main` function, we can initialize the SDK

```
require('dotenv').config()
const { mcsSDK } = require('js-mcs-sdk')

async function main() {
  // initialize js-mcs-sdk
  const mcs = await mcsSDK.initialize({
    apiKey: process.env.API_KEY,
    accessToken: process.env.ACCESS_TOKEN,
  })
}

main()
```

Optionally, you can pass `privateKey` to use the onChain Storage upload and payment functions and pass `rpcUrl` if you wish to use your own RPC URL (this SDK uses [https://polygon-rpc.com/](https://polygon-rpc.com/) by default).

This SDK is also compatible with our calibration environment on the Mumbai testnet. Use `chainName: 'polygon.mumbai'` and generate a new API KEY from [calibration-mcs.filswan.com](https://calibration-mcs.filswan.com/)

{% hint style="info" %}
Make sure the API Key and Access Token come from the same environment as `chainName`
{% endhint %}
