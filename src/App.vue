<template>
  <div id="app">
    <layout></layout>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import Layout from './components/Layout.vue'

  @Component({
    components: {
      Layout
    }
  })
export default class App extends Vue {}
</script>

<style lang="scss">
</style>
