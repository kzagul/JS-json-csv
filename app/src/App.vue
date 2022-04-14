
<template>
  <div id="app">
    <ExcelDownload />
  </div>
</template>

<script>
import "bootstrap/dist/css/bootstrap.min.css"
import "bootstrap-vue/dist/bootstrap-vue.css"

import Vue from "vue";
import JsonExcel from "vue-json-excel";
 
Vue.component("downloadExcel", JsonExcel);


import ExcelDownload from './components/ExcelDownload.vue'
export default {
  name: 'app',
  components: {
    ExcelDownload
  }
}
</script>