<template>
  <div class="max-w-md mx-auto flex p-12 bg-gray-100 mt-12 rounded-lg shadow-xl">
    <div class="mx-6 pt-1">
      <img class="object-scale-down h-48 w-full mb-12" src="/logo.png"/>
      <h1 class="text-2xl text-blue-700 leading-tight text-center">
        Rastreamento Correios
      </h1>
      <div v-if="mode === 'track'">
        <form class="w-full max-w-sm pt-4" @submit="track">
          <div class="flex items-center border-b border-blue-700 py-2">
            <input class="appearance-none bg-transparent border-none w-full text-gray-700 mr-3 py-1 px-2 leading-tight focus:outline-none" type="text" placeholder="Código de rastreamento" name="order" v-model="order"/>
            <button class="flex-shrink-0 bg-blue-700 hover:bg-blue-700 border-blue-700 hover:border-teal-700 text-sm border-4 text-white py-1 px-2 rounded" type="submit">
              Rastrear
            </button>
          </div>
        </form>
        <button class="object-scale-down w-full mt-6 bg-blue-700 hover:bg-blue-300 text-white font-semibold py-2 px-4 border border-gray-400 rounded shadow uppercase" v-on:click="see">
          Meus Pedidos
        </button>
      </div>
      <div v-else-if="mode === 'details'">
        <div>
          <div className="flex flex-wrap flex-col md:flex-row py-2">
            <Details :codigo="order"/>
          </div>
          <button class="object-scale-down w-full bg-blue-700 hover:bg-blue-300 text-white font-semibold py-2 px-4 border border-gray-400 rounded shadow uppercase" v-on:click="reset">
            Voltar
          </button>
        </div>
      </div>
      <div v-else>
        <div class="flex flex-wrap flex-col md:flex-row py-2">
          <Order v-for="ord in orders" :key="ord" :codigo="ord" @remove="onRemove($event)"  @details="onDetails($event)"/>
        </div>
        <button class="object-scale-down w-full bg-blue-700 hover:bg-blue-300 text-white font-semibold py-2 px-4 border border-gray-400 rounded shadow uppercase" v-on:click="reset">
          Voltar
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import Order from './Order.vue'
import Details from './Details.vue'

export default {
  name: 'Rastreador',
  components: {
    Order,
    Details
  },
  data: () => ({
    orders: [],
    order: null,
    mode: 'track'
  }),
  methods: {
    onRemove: function(o) {
      this.orders = this.orders.filter(function(order) {return order !== o});
      this.mode = 'track';
    },

    onDetails: function(o) {
      this.order = o;
      this.mode = 'details';
    },

    track: function(e) {
      if (!this.order) {
        this.errors.push('O código de rastreamento é obrigatório.');
      }else{
        this.orders.push(this.order);
        this.order = null;
        this.mode = 'orders';
      }
      e.preventDefault();
    },

    reset: function() {
      this.mode = 'track';
    },

    see: function() {
      this.mode = 'orders';
    }
  }
}
</script>

<style>

</style>
