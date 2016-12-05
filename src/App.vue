<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1 v-text='msg'></h1>
    <input type="text" v-on:keyup.enter='addlogin' v-model="inputtext"><br/>

    <ul>
      <li v-for='item in items' v-bind:class='{finished:item.isfinished}' v-on:click='toggle(item)'>
        {{item.label}}
      </li>
    </ul>
    <p>child tells me:{{childWords}}</p>
    <he msgfather='you d' v-on:child-tell='lishen'></he>
  </div>
  
</template>

<script>
import Stor from './storge';
import He from './components/Hello.vue'
export default {
  data() {
    return {
      msg: 'Welcome to Your Vue',
      inputtext:'',
      childWords:'',
      items: [
    
      ],
      items: Stor.fetch()
    }
  },
 components: {He},
watch: {
    items: {
      handler: function(val) {
        Stor.save(val);
      },
      deep: true
    }
  },
 methods:{
    toggle:function(item) {
      item.isfinished=!item.isfinished
    },
    addlogin:function() {
  
     this.items.push(
     {
     label:this.inputtext,
     isfinished:false
     }
     );
     this.inputtext='';
    },
    lishen:function(msg){
    console.log(msg);
    this.childWords = msg;
    }
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
.finished {
  color:red
}
</style>
