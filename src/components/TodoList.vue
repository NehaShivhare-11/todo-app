<template>
  <v-container>
    <v-row class="text-center">
      <v-col class="mb-4">
        <h1 class="display-2 font-weight-bold mb-3">
          To Do
        </h1>
        <v-container>
      <!-- <p>{{ selected }}</p> -->
      <v-checkbox
      class="m-n8 p-n8 border"
        v-for="todoItem in todoList"
        :key="todoItem.id"
        v-model="selected"
        :label="todoItem.todo"
        :value="todoItem.todo"
        @click="updateTodoList(todoItem)"
      ></v-checkbox>
    </v-container>
      </v-col>

    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios';
export default {
  name: 'TodoList',

  data: () => ({
    selected:'',
    base_url:'https://dummyjson.com/todos',
    todoList:[]
  }),
  created(){
    this.getTodoList();
  },
  methods:{
    getTodoList(){
      axios.get(this.base_url)
            .then( function( response){
              // eslint-disable-next-line no-debugger
                this.todoList = response.data.todos;
            }.bind(this))
            .catch( function( error ){
                this.axiosError = error;
            }.bind(this));
    },
    updateTodoList(item){
      setTimeout(() => {
        this.$emit('addSelectedTodo',item);
      let todo = this.todoList.filter(x=>x.id !== item.id);
      this.todoList = todo;
      }, 0);

    }
  }

}
</script>
<style scoped>
.border{
  border: 20px solid lightgray !important;
  height:90px;
}
</style>
