<template>
  <div class="home">
    <Factors msg="Welcome to Watch"/>
  </div>
</template>

<script>
// @ is an alias to /src
//import HelloWorld from '@/components/HelloWorld.vue'
import Factors from '@/components/12Factor.vue'

export default {
  name: 'HomeView',
  components: {
    Factors
  }
}
</script>
