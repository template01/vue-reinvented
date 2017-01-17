<template>
  <div class="">
    <h1>{{title}}</h1>
    <div class="single" v-bind:class="{ active: checked }">
      <h2>{{index}} a new project</h2>
      <code>{{checked}}</code>
      <code>{{index}}</code>
      <input v-on:click="toggleCheck" type="checkbox" v-bind:checked="checked">
      <p v-html="content"></p>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'singleproject',
    props: ['title', 'content', 'index', 'checked'],
    data() {
      return {
        projects: [],
        initState: this.checked

      }
    },
    methods: {
      toggleCheck: function() {
        console.log('baby' + this.index)
        this.$emit('toggleCheck')
      }
    },
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .active{
    background:red;
  }

  .single:not(.active){
    background: blue;
  }
  /*.not*/
</style>
