<template>
  <div>
    <div v-bind:key="td.id" v-for="td in todos">
        <TodoItem v-bind:todo="td" v-on:del-todo="$emit('del-todo', td.id)" />
    </div>
  </div>
</template>

<script>
import TodoItem from '@/components/TodoItem.vue'
export default {
    name: "Todos",
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script>

<style>
    * {
        box-sizing: border-box;
        margin: 0;
        padding: 0;
    }
    body {
        font-family: Arial, Helvetica, sans-serif;
        line-height: 1.4;
    }
</style>
