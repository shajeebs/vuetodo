<template>
  <div>
      <form @submit="addTodo">
          <input type="text" v-model="title" name="title" placeholder="Add ToDo..." />
          <input type="button" value="Submit" class="btn" />
      </form>
  </div>
</template>

<script>
export default {
    name:"AddTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e){
            e.preventDefault();
            
            const newTodo ={
                id: 1222,
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', newTodo);
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }
    input[type="text"]{
        flex:10;
        padding:5px;
    }
    input[type="submit"]{
        flex:2;
    }
</style>
