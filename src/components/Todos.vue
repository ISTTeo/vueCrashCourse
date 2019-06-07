<template>
    <div>
        <div class="row" v-for="row in Math.ceil(todos.length / 3)"> 
            <div class="col-md" v-bind:key="todo.id" v-for="todo in todos.slice((row - 1) * 3, row * 3)">
                <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/>
            </div>
        </div>
    </div>

    
</template>




<script>
import TodoItem from './TodoItem.vue';

export default {
    name: 'Todos',
    components: {
        TodoItem
    },
    props: ["todos"]
}
</script>

<style scoped>

</style>
