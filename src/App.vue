<template>
  <v-app>
    <v-main>
      <TodoPage :selectedTodoList="selectedTodoList"/>
      <TodoList @addSelectedTodo="addTodoItem"/>
      <p class="footer">Task board by Neha Shivhare</p>
    </v-main>
  </v-app>
</template>

<script>
import TodoPage from './components/TodoPage.vue'
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoList,
    TodoPage,
  },
  data: () => ({
    selectedTodoList:[]
  }),
  methods:{
    addTodoItem(todoItem){
      this.selectedTodoList.push(todoItem.todo);
    }
  }
}
</script>
<style scoped>
.footer{
  text-align: center;
  font-size: 21px;
  font-weight: 600;
}
</style>>
