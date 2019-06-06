<template>
    <div class="col-sm-6">
        <div class="card" style="width: 18rem;" v-bind:class="{'is-complete':todo.completed}">
            <div class="card-body">
                <h5 class="card-title"></h5>
                <h6 class="card-subtitle mb-2 text-muted">Card subtitle</h6>
                <p class="card-text">{{todo.title}}</p>
                <button v-on:click="$emit('del-todo', todo.id)" class="del">x</button>
            </div>
        </div>

    </div>
    
    <!-- <a class="todo-item" v-bind:class="{'is-complete':todo.completed}"> -->
        
<!--             <input type="checkbox" v-on:change="markComplete">  --> 
          <!-- {{todo.title.substring(0,2)+".."}} --> 
<!--             <button v-on:click="$emit('del-todo', todo.id)" class="del">x</button>
 -->        
    <!--  </a> -->
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
        background: #f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }

    .is-complete { 
        text-decoration: line-through;
    }

    .del {
        background: #ff0000;
        color: #fff;
        border: none;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float: right;
    }
</style>

