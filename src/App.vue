<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput @addTodoItem="addOneItem"></TodoInput>
    <TodoList :propsdata="todoItems"></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>

import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  
  name: 'App',
  components:  {
    TodoHeader, TodoFooter, TodoList, TodoInput
  },
  data() {
    return {
      todoItems: [] 
    }
  },
  created() {
        if (localStorage.length > 0 ) {
            for (let i =0; i < localStorage.length; i++) {
              this.todoItems.push(JSON.parse(localStorage.getItem(localStorage.key(i))))
      }
    }
  },
  methods: {
    addOneItem (todoItem) {
      const obj = { completed: false, item: todoItem}
      localStorage.setItem(todoItem, JSON.stringify(obj))
      this.todoItems.push(obj)
    }
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Itim&display=swap');

body {
  text-align: center;
  background-color: #F6F6F6;
}
input {
  border-style: groove;
  width: 200px;
}
button {
  border-style: groove;
}
.shadow {
  box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
}
html, body {
  font-family: 'Itim', cursive;
}
.shadow {
  box-shadow: 5px 1 px 1px rgba(0, 0, 0, 0.03);
}
#app {
  font-family: 'Itim', cursive;
}
</style>
