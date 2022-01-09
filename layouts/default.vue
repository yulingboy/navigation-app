<template>
  <div class="container">
      <div>
          <NavBar></NavBar>
      </div>
      <Nuxt />
  </div>
</template>

<script>
export default {

}
</script>

<style scoped>
.container {
    width: 100%;
    height: 100vh;
    background: url("@/assets/images/background.jpg") center center no-repeat;
    background-size: 100%;
    position: relative;
     /* -webkit-filter:blur(100) */
    
    /* -webkit-mask : -webkit-gradient(linear, left top, left bottom, from(rgba(0,0,0,1)), to(rgba(0,0,0,0))); */
}
/* .container::before {
    content: '';
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    z-index: 1;
    background-color: pink;
} */
</style>