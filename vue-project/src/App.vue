<template>
  <div id="app">
    <h2>{{msg}}</h2>
    <h3 v-text="msg"></h3>
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinished(item)">
        {{item.work}}
      </li>
    </ul>
  </div>
</template>

<script>
import Hello from './components/Hello'

export default {
  data (){
    return {
      msg:"第一个vue.js",
      items:[
        {
          work:"coding",
          isFinished:false
        },
        {
          work:"eating",
          isFinished:true
        }
      ],
    }
  },
  methods:{
    toggleFinished:function(item){
      return item.isFinished = !item.isFinished;
    }
  }
}
</script>

<style>
html {
  height: 100%;
}

body {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

#app {
  color: #2c3e50;
  margin-top: -100px;
  max-width: 600px;
  font-family: Source Sans Pro, Helvetica, sans-serif;
  text-align: center;
}
.finished{
  color: red;
}
#app a {
  color: #42b983;
  text-decoration: none;
}

.logo {
  width: 100px;
  height: 100px
}
</style>
