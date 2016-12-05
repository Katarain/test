<template>
<div class='hello'>
  <h1>{{ msg }}</h1>
  <h2>{{msgfather}}</h2>
  <button v-on:click='msgf'>chek</button>
</div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  props: ['msgfather'],
  methods:{
    msgf:function(){
    this.$emit('child-tell',this.msg);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

</style>
