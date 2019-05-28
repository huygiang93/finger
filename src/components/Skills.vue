<template>
  <div class="container">
    
    <div class="holder">
      
      <form @submit.prevent="addSkill">

        <input type="text" placeholder="Add a skill you have here..."  v-model="skill" v-validate="'min:3'" name="skill">
        
        <transition name="alert-in" enter-active-class="animateflipInX" leave-active-class="animated flipOutX">
          <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        </transition>

      </form>


      <ul>
        <li v-for="(data, index) in skills" :key='index'>{{data.skill}}
          <i class="fa fa-minus-circle" v-on:click="remove(index)"></i>
        </li>
      </ul>

      <p>These are the skills that you possess.</p>

      
    </div>
        <!--crazy button-->
      <a class="button is-info is-crazy"
      :style="buttonOffsets"
      @mouseenter="moveButton">
        click me for $5
      </a>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data(){
    return{
      skill:'',
      skills: [
        {"skill": "Vue.js"},
        {"skill": "Frontend Developer"}
      ],
      buttonOffsets:{
        top:null,
        left:null
      }
    }
  },
  methods : {
    addSkill(){
      this.skills.push({skill: this.skill});
      this.skill='';
    },
    remove(id){
      this.skills.splice(id,1);
    },
    moveButton(){
      this.buttonOffsets={
        top:`${Math.random()*window.innerHeight}px`,
        left:`${Math.random()*window.innerWidth}px`,
      }
    },
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css"; 


  .is-info{
    padding: 10px;
    background-color: #3273dc;
    border-color:transparent;
    color:#fff;
  }
  .is-crazy{
    position:absolute;
    transition:0.3s ease all;
  }

  .holder {
      background: #fff;
    }

  ul {
    margin: 0;
    padding: 0;
    list-style-type: none;
  }

  ul li {
    padding: 20px;
    font-size: 1.3em;
    background-color: #E0EDF4;
    border-left: 5px solid #3EB3F6;
    margin-bottom: 2px;
    color: #3E5252;
  }

  p {
    text-align:center;
    padding: 30px 0;
    color: gray;
  }

  .container {
    box-shadow: 0px 0px 40px lightgray;
  }

  input {
    width: calc(100% - 40px);
    border: 0;
    padding: 20px;
    font-size: 1.3em;
    background-color: #323333;
    color: #687F7F;
  }

  .alert {
    background: #fdf2ce;
    font-weight: bold;
    display: inline-block;
    padding: 5px;
    margin-top: -20px;
  }

  .alert-in-enter-active{
    animation:bounce-in .5s;
  }

  .alert-in-leave-active{
    animation:bounce-in .5s reverse;
  }
  @keyframes bounce-in{
    0%{
      transform:scale(0);
    }
    50%{
      transform:scale(1.5);
    }
    100%{
      transform: scale(1);
    }
  
  }

</style>
