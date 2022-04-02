<template>
  <div class="home">
    <HelloWorldBoostrap msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorldBoostrap from '@/components/HelloWorldBoostrap.vue'

export default {
  name: 'HomeView',
  components: {
    HelloWorldBoostrap
  }
}
</script>
