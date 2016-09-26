<template>
  <div id="app">
    <h2>{{msg}}</h2>
    <input type="text" v-model="newItem" v-on:keyup.enter="addNew">
    <h3 v-text="msg"></h3>
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinished(item)">
        {{item.work}}
      </li>
    </ul>
    <p>{{newItem}}</p>

    <p>{{message}}</p>
    <button v-on:click="reverseMessage">Resverse Message</button>
    <hr />
    <!-- 综合 todo list  -->
    <input v-model="newTodo" type="text" v-on:keyup.enter="addTodo">
    <ul>
      <li v-for="todo in todos">
        <span>{{todo.text}}</span>
        <button v-on:click="removeTodo($index)">del</button>
      </li>
    </ul>
  </div>
</template>

<script>
// import Hello from './components/Hello'

export default {
  data (){
    return {
      msg:"第一个vue.js",
      items:[],
      newItem:"",
      message:"hello Vue",
      newTodo:"",
      todos:[
        {text:"第一个todolist"}
      ]
    }

  },
  methods:{
    toggleFinished:function(item){
      return item.isFinished = !item.isFinished;
    },
    addNew:function(){
      this.items.push({
        work:this.newItem,
        isFinished:false
      });
      this.newItem = "";
    },
    reverseMessage:function(){
      this.message = this.message.split("").reverse().join("");
    },
    addTodo:function(){
      var text = this.newTodo.trim();
      if(text){
        this.todos.push({text:text});
        this.newTodo="";
      }
    },
    removeTodo:function(index){
      this.todos.splice(index,1)
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
