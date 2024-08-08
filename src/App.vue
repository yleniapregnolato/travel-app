<script>
import AppHeader from "./components/AppHeader.vue";
export default {
  components: {
    AppHeader
},
};
</script>

<template>
  <div class="container-fluid" id="app">
    <AppHeader />
  </div>
</template>

<style lang="scss">
.container-fluid {
  background-image: url('src/assets/img/palme.jpeg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  height: 100vh;
  width: 100%;
}

.container-fluid::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.15);
}

#app > * {
  position: relative;
  z-index: 2; 
}
</style>