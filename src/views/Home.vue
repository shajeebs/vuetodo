<template>
  <div class="home">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todoData" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
// @ is an alias to /src
import Todos from '@/components/Todos.vue'
import AddTodo from '@/components/AddTodo.vue'
import axios from 'axios';

export default {
  name: 'home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todoData: []
    }
  },
  methods: {
    deleteTodo(id) {
      //console.log('Hello' + id);
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => this.todoData = this.todoData.filter(td => td.id != res.data.id));
        //.catch(err);
    }, 
    addTodo(newTodo){
     // console.log('Hello');
      //console.log(newTodo);
      const { title, completed } = newTodo;
     
      axios.post('https://jsonplaceholder.typicode.com/todos', { title, completed})
        .then(res => this.todoData = [...this.todoData, res.data]);
        //.catch(err);

      this.todoData = [...this.todoData, newTodo];
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todoData = res.data);
      //.catch(err);
  }
}
</script>

<style scoped>
  .btn {
    display:inline-block;
    border:none;
    background:#555;
    color:white;
    padding:7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background:yellowgreen;
  }
</style>
