<template>
  <div class="stock-item sell">
    <div class="stock-item__title sell">
      <span class="stock-item__name sell">{{ name }}</span>
      <span class="stock-item__price sell">(Price: {{ price }} | Quantity: {{ quantity }})</span>
    </div>
    <div class="stock-item__body sell">
      <input type="number" placeholder="Quantity" v-model="selling">
      <button @click="sell({ name, quantity: Math.abs(selling) })" :class="{ 'activate': selling, 'sell': true }">Sell</button>
    </div>
  </div>
</template>

<script>
  export default {
      data() {
        return {
          selling: '',
        }
      },
      props: ['name', 'price', 'quantity'],
      methods: {
        sell(obj) {
          this.$store.dispatch('sell', obj);
          this.selling = '';
        }
      },
  }
</script>

<style scoped>

  .stock-item__title.sell {
    background: lightblue;
  }

  .stock-item__name.sell {
    color: #444496;
  }

  .stock-item__price.sell {
    color: #444496;
  }

  .stock-item__body.sell {
    border-color: lightblue;
  }

  .stock-item__body.sell > input:focus {
    outline-color: lightblue;
  }

  .stock-item__body.sell > button {
    background: lightcoral;
    border-color: lightcoral;
  }

  button.activate.sell {
    background: #dd4242;
    border-color: #dd4242;
  }

</style>