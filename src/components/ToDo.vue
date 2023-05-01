<template>
        <div>
            <input type="text" v-model="new_todo"> <button v-on:click=" addNewTodo()"> ADD </button>
            <h2> To Do </h2>
            <ul>
                <li v-for="todo in todo_list" v-bind:key="todo.id" :class="{done: todo.isDone}"> 
                    {{ todo.title }} 
                    <button v-on:click="doneTodo(todo.id)"> 
                        <span v-if="!todo.isDone"> &#9745; </span>
                        <span v-if="todo.isDone"> &#9746; </span>
                    </button> 
                </li>
            </ul>
            <button v-on:click="clearDoneTasks()"> Clear done tasks</button>
        </div>
</template>

<script>
    export default {
        data () {
            return {
                new_todo: '',
                todo_list: [],

            }
        },
        methods: {
            addNewTodo() {
                if(this.new_todo == ''){
                    return;
                }
                this.todo_list.push({title: this.new_todo, isDone: false, id: Math.round(Math.random()*10000000)});
                this.new_todo = '';

            },
            doneTodo(id){
                this.todo_list.forEach(e => {
                    e.id == id ? e.isDone = !e.isDone: 0;
                });
            },
            clearDoneTasks(){
                let notDoneTasks = this.todo_list.filter( e => !e.isDone);
                this.todo_list = notDoneTasks;
            }

        }
    }
</script>

<style lang="scss">
    .done{
        text-decoration: line-through;
    }
</style>