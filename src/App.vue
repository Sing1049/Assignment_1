<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h2>Claim Request Form</h2>
    <br>
      <!-- data from component is displayed down -->
    <ClaimForm />
    
      <!-- data finshed-->

        <!-- After this is useless just to add my name with some <br> tag to add extra space  -->
    <br>
    <br>
    <br>
    <br>
    <br>
    <br>
    <hr>
    <p>Assignment By <a href="mailto:sing1049@algonquinlive.com">Gurjeet Singh</a> </p>
  </div>
</template>

<script>
  // component imported 
import ClaimForm from './components/form.vue';
export default {
  name: 'app',
  data() {
    return {
      input : "" 
    }
  },
  components: {
    ClaimForm
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#app a {
  text-decoration: none;
  color: inherit;
}
#app a:hover {
  border-top: 3px solid orange;
  padding-top: 3px;
}
</style>
