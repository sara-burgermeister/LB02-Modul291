<template>
  <div>
    <h2>Products</h2>
    <table>
      <thead>
      <tr>
        <th>Name</th>
        <td>&nbsp;&nbsp;&nbsp;</td>
        <th>Price</th>
        <th>&nbsp;</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="(product, idx) in products" :key="idx">
        <td>{{ product.name }}</td>
        <td>&nbsp;&nbsp;&nbsp;</td>
        <td>{{ product.price.toFixed(2) }}</td>
        <td>&nbsp;&nbsp;&nbsp;</td>
        <td>
          <b-button variant="success"  @click="addToCart(product)">+</b-button>
          <b-button variant="danger" @click="removeFromCart(product)">-</b-button>
        </td>
      </tr>
      </tbody>
    </table>
    <br>
    <br>
    <div>
      <h3 v-if="false" v-text="text1">Loading...</h3>
      <h3 v-else-if="false" v-text="text2">Loading...</h3>
      <h3 v-else v-text="text3">Loading...</h3>
      <a
          :href="link.url"
          :target="link.target"
          :tabindex="link.tabindex"
          v-text="link.title"
      />
    </div>
  </div>
</template>

<script>
import { mapState } from 'vuex';
export default {
  name: 'Products',
  computed: mapState(['products']),
  methods: {
    addToCart(product) {
      this.$store.commit('addToCart', product);
    },
    removeFromCart(product) {
      this.$store.commit('removeFromCart', product);
    }
  },
  created() {
    this.$store.dispatch("loadProducts")
  },
  data() {
    return {
      // v-text
      text1: 'Hier gehts zum Helpdesk',
      text2: 'Voici le service d\'assistance',
      text3: 'Ecco l\'helpdesk',
      // v-bind
      link: {
        url: 'https://www.officeworld.ch/de/kontakt/fragen',
        target: '_blank',
        tabindex: '0',
        title: 'Helpdesk',
      },
    }
  },
}
</script>
