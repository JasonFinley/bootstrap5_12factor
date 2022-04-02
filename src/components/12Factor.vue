<template>
<nav class="navbar navbar-expand-lg navbar-light">
  <div class="container-fluid bg-warning">
    <div class="collapse navbar-collapse bg-dark text-white" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
            <div class="h4 text-start" v-for="(item, index) in title" v-bind:key="index">{{ item }}
              <div class="h6 text-start">{{ sub[index] }}</div></div>
        </li>
      </ul>
    </div>
    <div class="bg-while text-start">{{ pareLordFile( info ) }}</div>
  </div>
</nav>
</template>

<script>
import Logs12 from '../assets/Logs.txt'

var factorTitle = {
    0 : "I. Codebase",
    1 : "II. Dependencies",
    2 : "III. Config",
    3 : "IV. Backing services",
    4 : "V. Build, release, run",
    5 : "VI. Processes",
    6 : "VII. Port binding",
    7 : "VIII. Concurrency",
    8 : "IX. Disposability",
    9 : "X. Dev/prod parity",
    10 : "XI. Logs",
    11 : "XII. Admin processes"
};

var factorSub = {
    0 : "One codebase tracked in revision control, many deploys",
    1 : "Explicitly declare and isolate dependencies",
    2 : "Store config in the environment",
    3 : "Treat backing services as attached resources",
    4 : "Strictly separate build and run stages",
    5 : "Execute the app as one or more stateless processes",
    6 : "Export services via port binding",
    7 : "Scale out via the process model",
    8 : "Maximize robustness with fast startup and graceful shutdown",
    9 : "Keep development, staging, and production as similar as possible",
    10 : "Treat logs as event streams",
    11 : "Run admin/management tasks as one-off processes",
};

function pareMyLordFile( loadFileTxt ){
  console.log( loadFileTxt.replace(/\\r\\n/g, '<br>') );
  console.log( "loadFileTxt" );
  console.log( {loadFileTxt });
  return loadFileTxt;//loadFileTxt.replace(/(\\r)*\\n/g, '<br>');
}

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return { 
      title : factorTitle, 
      sub : factorSub, 
      info : Logs12, 
    };
  },
  methods:{
    pareLordFile : pareMyLordFile,
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

@import "~bootstrap/scss/bootstrap";

</style>
