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