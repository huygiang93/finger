<template>
  <div id="app">
    <nav>
        <router-link to="/">Home</router-link>
        <router-link to="/about">About</router-link>
      <h1 @click="onClick">
        {{message}}
      </h1>
      </nav>

    <router-view/>
<!--     <Skills/> -->
    

  </div>
</template>

<script>
/* import Skills from './components/Skills.vue' */
import Vue from 'vue';
import Component from 'vue-class-component';


export default Component({})(
  class App extends Vue{
    message = 'Click here to reveal author of this page';

    onClick(){
      this.message = "Huy Giang";
    }
  }
)
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Montserrat:400,700');


body {
  background-color: #EEEEEE;
  font-family: 'Montserrat', sans-serif;
  display: grid;
  grid-template-rows: auto;
  justify-items: center;
  padding-top: 50px;
  }

h1{
  padding: 10px;
  border-radius:3px;

}
nav {
  padding: 20px 20px 20px 0;
}

nav a {
  padding: 10px;
  text-decoration: none;
  background: #fff;
  border-radius: 3px;
  color: rgb(0, 110, 255);
  font-weight: bold;
  margin-right: 15px;
}

body, html {
  margin: 0;
  height: 100%;
}

#app {
/*   font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
  width:50%
}


/* h1{
  padding:0px;
  text-decoration: navajowhite;
  background: rgb(112, 233, 101);
  color: rgb(219, 18, 18);
  
} */


</style>
