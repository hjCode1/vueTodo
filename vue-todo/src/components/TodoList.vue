<template>
  <div>
      <ul>
        <li v-for="(todoItem, index) in todoItems" v-bind:key="todoItem.item" class="shadow">
          <i class="checkBtn fas fa-check" v-bind:class="{checkBtnComplete : todoItem.completed}" 
              v-on:click="toggleComplete(todoItem)"></i>
          <span v-bind:class="{textCompleted : todoItem.completed}">{{ todoItem.item }}</span>
          <span class="removeBtn" v-on:click="removeTodo(todoItem, index)">
            <i class="fas fa-trash-alt"></i>
          </span>
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  data: function(){
    return {
      todoItems: []
    }
  },
  methods: {
    removeTodo: function(todoItem, index){
      // console.log(todoItem ,index);
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    toggleComplete: function(todoItem){
      console.log(todoItem);
      todoItem.completed = !todoItem.completed;
      localStorage.removeItem(todoItem.item);
      localStorage.setItem(todoItem.item, JSON.stringify(todoItem))
    }
  },
  // 인스턴스가 생성되자마자 생성되는 라이프사이클 hook => created
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
  }
}
</script>

<style scoped>
ul {
  list-style: none;
  padding:0;
  margin:0;
  text-align: left;
}
li {
  display:flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding:0 0.9rem;
  background: #fff;
  border-radius: 5px;
}
.checkBtn {
  line-height: 45px;
  color:#62acde;
  margin-right: 5px;
}
.checkBtnComplete {
  color: #b3adad;
}
.removeBtn {
  margin-left:auto;
  color:#de4343;
  cursor: pointer;
}
.textCompleted {
  text-decoration: line-through;
  color:#b3adad;
}
</style>