<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>{{fatherMsg}}</h2>
    <button v-on:click="onClickMe">onClickMe</button>
  </div>
</template>

<script>
export default {
  data:function() {
    return {
      msg: 'componentA test'
    }
  },
  props:['father-msg'],
  methods:{
    onClickMe:function(){
      alert(this.fatherMsg)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->

<style scoped>
h1 {
  color: #42b983;
}
</style>
<!--
  1:引入组件import componentA from './components/componentA';
  2:写明依赖 components:{componentA},
  3:在html上写出位置 <component-a></component-a>
-->