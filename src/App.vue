<template>
  <div id="app">
    <Header />
    <router-view/>
  </div>
</template>

<script lang="ts">
import Header from './components/layouts/Header.vue'
import Vue from 'vue'

export default Vue.extend({
  name: 'app',
  components: {
    Header
  }
})
</script>


<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    background: #e8f7f0;
    font-family: Arial, helvetica, sans-serif;
    line-height: 1.6;
  }

  .btn {
    display: inline-block;
    background: #555;    
    border: none;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }

  .container {
    max-width: 1100px;
    margin: auto;
    overflow: auto;
    padding: 0 2rem;
  }
</style>
