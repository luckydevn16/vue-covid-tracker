<template>
  <header class="header">
    <h3 class="header-heading">
      <img src="../assets/img/virus.png" alt="virus" class="header-img">
      Covid-19 Tracker
    </h3>
    <p>API by <a href="https://covid19api.com" target="_blank" class="header-link">covid19api.com</a></p>
  </header>
</template>

<script>
export default {
  name: 'Header',
}
</script>

<style>
.header {
  background-color: #145DBF;
  color: #fff;
  display: grid;
  place-items: center center;
  padding: 1rem;
  box-shadow: 0 3px 8px #999
}
.header h3 {
  font-size: 2rem;
  font-weight: 300;
  display: flex;
  align-items: center;
}
.header-img {
  width: 2.5rem;
  height: auto;
  margin-right: .5rem;
}
.header p {
  font-size: .8rem;
  line-height: 150%;
}
.header-link {
  color: #a6c8f5
}
</style>
