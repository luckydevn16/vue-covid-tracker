<template>
  <Header />
  <Home />
</template>

<script>
import Header from '@/components/Header';
import Home from '@/components/Home';

export default {
  components: {
    Header, Home
  }
}
</script>


<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
a {text-decoration: none;color:inherit}
#app {
  font-family: Arial, sans-serif;
}
.container {
  width: 90%;
  max-width: 800px;
  margin: 0 auto;
}
</style>
