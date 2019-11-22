<template>
  <div id="app">
    <Header/>
    <div class="columns">
      <div class="column is-narrow">
        <SideMenu/>
      </div>
      <div class="column">
        <StashTable/>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
//import Tea from './components/Tea.vue'
import SideMenu from './components/SideMenu.vue'
import StashTable from './components/StashTable.vue'

export default {
  name: 'app',
  components: {
    Header,
    StashTable,
    SideMenu
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
</style>
