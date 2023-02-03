<template>
    <v-container>
      <v-row class="text-center">  
        <v-col class="mb-4">
          <h1 class="display-2 font-weight-bold mb-3">
            I did it!
          </h1>
          <v-container>
            <div>
      <v-card 
        class="d-flex align-content-space-around flex-wrap"
        color="#40b14478"
        flat
        tile
        min-height="200"
      >
        <v-card
          v-for="n in selectedTodoList"
          :key="n"
          class= "pa-md-4 mx-lg-auto w-125 my-2"
          outlined
          tile
        >
          {{ n }}
        </v-card>
      </v-card>
    </div>
      </v-container>
  
  <!-- 
          <p class="subheading font-weight-regular">
            For help and collaboration with other Vuetify developers,
            <br>please join our online
            <a
              href="https://community.vuetifyjs.com"
              target="_blank"
            >Discord Community</a>
          </p> -->
        </v-col>
      </v-row>
    </v-container>
  </template>
  
  <script>
  import axios from 'axios';
  export default {
    name: 'TodoPage',
    props: {
        selectedTodoList: {
            type: Array,
        },
    },
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
                debugger;
                  this.todoList = response.data.todos;
              }.bind(this))
              .catch( function( error ){
                  this.axiosError = error;
              }.bind(this));
      }
    }
  
  }
  </script>
  <style scoped>
  .w-125{
    width:15%
  }
  </style>>
  