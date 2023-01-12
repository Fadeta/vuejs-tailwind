<script>
export default {
  data() {
    return {
      listsuhu: [],
    }
  },
  methods:{
   
   async ambildata() {
     const response = await fetch("http://localhost:3000/getlist");
     const data = await response.json();
     this.listsuhu = data.sensor_suhu;
     console.log( this.listsuhu[0] );
   }
 }

}


</script>
<style>
#app {
  max-width: 1280px;
  margin: 0 auto;
  padding: 2rem;

  font-weight: normal;
}
</style>

<template>
<div class="relative overflow-x-auto shadow-md sm:rounded-lg">
  <table class="w-full text-sm text-left text-blue-100 dark:text-blue-100 text-xs text-white uppercase bg-blue-600 dark:text-white">
    <tr>
      <td scope="col" class="px-6 py-3">Waktu</td>
      <td scope="col" class="px-6 py-3">Suhu</td>
    </tr>
    <tr v-for="item in listsuhu">
      <td scope="col" class="px-6 py-3">{{ item.waktu }}</td>
      <td scope="col" class="px-6 py-3">{{ item.suhu }}</td>
    </tr>
  </table>
</div>
  <div class="flex items-center justify-center">
    <button class="pointer-events-auto rounded-md bg-indigo-600 py-2 px-3 text-[0.8125rem] font-semibold leading-5 text-white hover:bg-indigo-500" 
    @click="ambildata()">
    Ambil Data
  </button>
  </div>
</template>