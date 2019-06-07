<template>
    
        
        <div class="card todo-item" >
            <div class="card-header" v-if="todo.completed" v-on:click="markComplete">
                <div class="btn-group" data-toggle="buttons">
                    <label class="btn btn-warning active">
                        Unmark as Completed
                        <input type="checkbox" name="" id="" checked autocomplete="off">
                    </label>
                    
                </div>
                

            </div>
            <div class="card-header" v-if="!todo.completed" v-on:click="markComplete">
                
                <div class="btn-group" data-toggle="buttons">
                    <label class="btn btn-success">
                        Mark as Completed
                        <input type="checkbox" name="" id=""  autocomplete="off">
                    </label>
                    
                </div>
            </div>
            <div class="card-body" style="background:#9299a3"  v-bind:class="{'is-complete':todo.completed}">{{todo.title}}</div> 
            <div class="card-footer " >
                <a class="btn btn-danger" v-on:click="$emit('del-todo', todo.id)"  role="button">Delete</a>
                
            </div>
        </div>
    
    
<!-- <a class="todo-item" v-bind:class="{'is-complete':todo.completed}"> associa a classe is-complete -->
        
<!-- <input type="checkbox" v-on:change="markComplete"> --> 

<!-- <button v-on:click="$emit('del-todo', todo.id)" class="del">x</button> --> 
        

</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
    
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;

        }
    }
}
</script>

<style scoped>
    .todo-item {
        margin-top: 10px;
        margin-bottom: 10px;
        text-align: center;
        background: 
    }

    .is-complete { 
        text-decoration: line-through;
        color:grey;
        background: black !important;
    }

    .del {
        background: #ff0000 !important;
        opacity: 80%;
    }
</style>

