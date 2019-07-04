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

export default {
  name: 'home',
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todoData: [
        { id: 1, title: "Todo One", completed:false },
        { id: 2, title: "Todo Two", completed:false },
        { id: 3, title: "Todo Three", completed:true },
        { id: 4, title: "Todo Four", completed:false },
        { id: 5, title: "Todo Five", completed:true },
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todoData = this.todoData.filter(td => td.id != id);
    },
    addTodo(newTodo){
      this.todoData = [...this.todoData, newTodo];
    }
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
