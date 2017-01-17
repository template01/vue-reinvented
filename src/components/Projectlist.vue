<template>
  <div class="">
    <!-- <input type="checkbox" v-model="checked"> -->
    <div v-for="(project, index) in projects">
    <input type="checkbox" v-on:click="toggleCheckParent(index)"   v-model="projectsChecked[index]">

      <!-- {{#if this.projectsChecked[index]}} -->
      <!-- <code  v-if="projectsChecked[index]">Yes</code> -->
      <!-- <code  v-else="projectsChecked[index]">no</code> -->
      <!-- {{/if}} -->
    </div>
    <div v-for="(project, index) in projects">
      <singleproject v-on:toggleCheck="toggleCheckParent(index)" v-bind:index="index" v-bind:checked="projectsChecked[index]" v-bind:title="project.title.rendered" v-bind:content="project.excerpt.rendered" ></singleproject>
    </div>

<input type="checkbox" v-on:click="toggleCheckParent(index)"  v-for="(project, index) in projects" v-model="projectsChecked[index]">

  </div>
</template>

<script>
  import Singleproject from './Singleproject'

  export default {
    name: 'projectlist',
    components: {
      Singleproject,
    },
    data() {
      return {
        checked: true,
        projects: [],
        projectsChecked: [false, false, false, false]
      }
    },
    created: function() {
      console.log('yesa')
      this.$http.get('http://api.template-studio.nl/wp-json/wp/v2/posts').then(function(response) {
        console.log(response)

        this.projects = response.body
      })
    },
    methods: {
      toggleCheckParent: function(index) {
        console.log('check parent' + index)
        this.$set(this.projectsChecked, index, this.toggleChecked(index))
      },
      toggleChecked: function(index) {
        return this.projectsChecked[index] = !this.projectsChecked[index]


      }
    }
  }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
