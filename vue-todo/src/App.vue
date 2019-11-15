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
