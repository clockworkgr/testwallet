<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import { SigningStargateClient } from '@cosmjs/stargate';

const doSomething = async () => {
  console.log("what");
  const x = window.nephos.enable(["cosmoshub-4"]);
  console.log(x);
  await x;
  const client = await SigningStargateClient.connectWithSigner("wss://cosmos-rpc.polkachu.com", await window.nephos.getOfflineSigner("cosmoshub-4"));
  console.log(client);
  const res = await client.sendTokens("cosmos1995thtfe5gs47wrrjg9gsq0xs0udq3lrlasttl", "cosmos13lr7pgzv5mrkca2gx2xly5ffw2rzes58wd37y7", [{ amount: "10", denom: "uatom" }], { amount: [{ amount: "1000", denom: "uatom" }], gas: "200000" }, "Signed with Castor");
  console.log(res);
  /*
  window.keplr.experimentalSuggestChain({
    "rpc": "https://rpc.test4.gno.land",
    "chainId": "test4",
    "chainName": "Test 4 gnoland",
    "bip44": {
      "coinType": 118
    },
    "bech32Config": {
      "bech32PrefixAccAddr": "g",
      "bech32PrefixAccPub": "gpub",
      "bech32PrefixValAddr": "gvaloper",
      "bech32PrefixValPub": "gvaloperpub",
      "bech32PrefixConsAddr": "gvalcons",
      "bech32PrefixConsPub": "gvalconspub"
    },
    "currencies": [
      {
        "coinDenom": "GNOT",
        "coinMinimalDenom": "ugnot",
        "coinDecimals": 6
      }
    ],
    "stakeCurrency": {
      "coinDenom": "GNOT",
      "coinMinimalDenom": "ugnot",
      "coinDecimals": 6
    },
    "feeCurrencies": [
      {
        "coinDenom": "GNOT",
        "coinMinimalDenom": "ugnot",
        "coinDecimals": 6
      }
    ]
  }
  )
*/
}
</script>

<template>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
    <button @click="doSomething">TESTTESTTEST</button>
  </main>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
