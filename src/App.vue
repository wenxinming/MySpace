<template>
  <NavBar></NavBar>
  <router-view/>
</template>

<script>
import NavBar from './components/NavBar.vue';
import  'bootstrap/dist/css/bootstrap.css';
import 'bootstrap/dist/js/bootstrap';
export default {
  name:"APP",
  components:{
    NavBar
  }
}
</script>



<style>

</style>
