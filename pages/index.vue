<template>
  <section class="section">
    <div class="columns is-mobile">
      <card
        title="Free"
        icon="github-circle"
      >
        Open source on <a href="https://github.com/buefy/buefy">
          GitHub
        </a>
      </card>

      <card
        title="Responsive"
        icon="cellphone-link"
      >
        <b class="has-text-grey">
          Every
        </b> component is responsive
      </card>

      <card
        title="Modern"
        icon="alert-decagram"
      >
        Built with <a href="https://vuejs.org/">
          Vue.js
        </a> and <a href="http://bulma.io/">
          Bulma
        </a>
      </card>

      <card
        title="Lightweight"
        icon="arrange-bring-to-front"
      >
        No other internal dependency
      </card>
    </div>
  </section>
</template>

<script>
import Card from '~/components/Card'
    const Web3Utils = require("web3-utils");
    const bn128 = require("snarkjs").bn128;

export default {
  name: 'HomePage',

  components: {
    Card
  },
  mounted() {

    const F = bn128.Fr;

    const SEED = "mimcsponge";
    let c = Web3Utils.keccak256(SEED);
    c = Web3Utils.keccak256(c);

    const n1 = Web3Utils.toBN(c).mod(Web3Utils.toBN(F.q.toString()));
    // const n1 = Web3Utils.toBN('7120861356467848435263064379192047478074060781135320967663101236819528304084')
    console.log('n1', n1.toString())
    const toX = Web3Utils.toHex(n1)
    console.log('toX', toX)
  }
}
</script>
