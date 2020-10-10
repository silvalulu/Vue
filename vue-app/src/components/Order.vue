<template>
  <div>
    <div class="flex flex-wrap bg-white border-b border-blue-tial-100">
      <div class="flex w-full m-4">
        <div class="flex items-center">
          <div class="flex flex-col p-4">
            <h3 class="font-bold text-md text-tial-400">{{ codigo }}</h3>
            <span class="font-light text-sm">Objeto entregue ao destinatário</span>
            <div class="flex">
            </div>
          </div>
        </div>
        <div class="flex flex-1 flex-grow w-full items-center justify-end">
          <div class="flex items-center mr-2 space-x-4">
          <button class="bg-gray-300 hover:bg-gray-400 font-bold  text-red-700 py-2 px-4 rounded inline-flex items-center" @click="detailed()">
            <span class="text-lg uppercase font-semibold text-green-700 hover:text-green-300">Detalhes</span>
          </button>
          <button class="bg-gray-300 hover:bg-gray-400 font-bold  text-red-700 py-2 px-4 rounded inline-flex items-center" @click="removed()">
            <span class="text-lg uppercase font-semibold text-red-700 hover:text-blue-300">Remover</span>
          </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Order',
  props: ['codigo'],
  methods: {
        removed: function() {
            console.log(this.codigo)
            this.$emit('remove', this.codigo)
        },
        detailed: function() {
            console.log(this.codigo)
            this.$emit('details', this.codigo)
        }
  }
}
</script>

<style>

</style>
