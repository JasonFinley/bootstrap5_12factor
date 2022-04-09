<template>
  <div class="home">
    <MVMayDay msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import MVMayDay from '@/components/MayDay.vue'

export default {
  name: 'HomeView',
  components: {
    MVMayDay
  }
}
</script>