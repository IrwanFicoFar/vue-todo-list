<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png" />
    <HelloWorld msg="Welcome to Your To Do List App" />
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

import "bootstrap/dist/css/bootstrap.css";

export default {
  name: "HomeView",
  components: {
    HelloWorld,
  },
};
</script>
