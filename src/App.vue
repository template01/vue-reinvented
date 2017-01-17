<template>
  <div id="app">
    <projectlist></projectlist>
  </div>
</template>

<script>
import Hello from './components/Hello'
import Projectlist from './components/Projectlist'

export default {
  name: 'app',
  components: {
    Hello,
    Projectlist,
  }
}
</script>

<style>

</style>
