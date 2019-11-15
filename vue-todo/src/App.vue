<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  data: function(){
    return {
      todoItems: []
    }
  },
  created: function(){
    // console.log('create')
    if( localStorage.length > 0 ){ 
      for( var i = 0; i < localStorage.length; i++ ){
        if( localStorage.key(i) !== 'loglevel:webpack-dev-server' ){
          this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))));
          // this.todoItems.push(localStorage.key(i));
        }
      }
    }
  },
  components: {
    // '태그명' : 컴포넌트 명
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter
  }
}
</script>

<style>
body {
  background: #ebebeb;
  text-align: center;
}
input {
  border-style:groove;
  width:300px;
}
button {
  border-style:groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0,0,0,0.2);
}
</style>
