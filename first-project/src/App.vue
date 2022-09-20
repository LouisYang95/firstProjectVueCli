<template>
  <ActualHour />
  <Dashboard />
</template>

<script>
import ActualHour from './components/Hour.vue'
import Dashboard from './components/Dashboard.vue'

export default {
  name: 'App',
  components: {
    ActualHour,
    Dashboard
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
