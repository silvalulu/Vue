<template>
  <div>
    <h2 class="font-bold text-md text-tial-400">{{ codigo }}</h2>
    <div class="flex flex-wrap bg-white border-b border-blue-tial-100">
      <div class="flex w-full m-4">
        <div class="flex items-center">
          <div class="flex flex-col p-4">
            <span class="font-light text-sm">Objeto saiu para entregar</span>
            <div class="flex">
            </div>
          </div>
        </div>
      </div>
      <div class="flex w-full m-4">
        <div class="flex items-center">
          <div class="flex flex-col p-4">
            <span class="font-light text-sm">Objeto entregue ao destinatário</span>
            <div class="flex">
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Details',
  props: ['codigo']
}
</script>

<style>

</style>
