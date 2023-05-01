<template>
        <div class="C-ToDo-box">
            <div>
                <div class="C-ToDo-box__form">
                    <input type="text" v-model="new_todo" placeholder="New task" class="C-ToDo-box__form__input"> <button v-on:click=" addNewTodo()" class="C-ToDo-box__form__add-button"> ADD </button>
                </div>
                <div class="C-ToDo-box__list-container">
                    <h2> Tasks</h2>
                    <ul>
                        <li v-for="todo in todo_list" v-bind:key="todo.id" > 
                            <span :class="{done: todo.isDone}">- {{ todo.title }}</span>
                            <button v-on:click="doneTodo(todo.id)" class="C-ToDo-box__list-container__button"> 
                                <span v-if="todo.isDone"> &#9745; </span>
                                <span v-if="!todo.isDone"> &#9746; </span>
                            </button> 
                        </li>
                    </ul>
                </div>
            </div>
            <button v-on:click="clearDoneTasks()" class="C-ToDo-box__clear-button"> Clear done tasks</button>
        </div>
</template>

<script>
    export default {
        data () {
            return {
                new_todo: '',
                todo_list: [{
                    title: "Do sth",
                    isDone: false,
                    id: 123455
                }
                ],

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
    $bc: #82969065;
    $hoverBc: rgb(3, 105, 71);
    .done{
        text-decoration: line-through rgb(209, 42, 42) 3px;
    }
    .C-ToDo-box{
        width: 500px;
        min-height: 600px;
        max-height: 1000px;
        border-radius: 30px;
        background-color: $bc;
        padding: 20px;
        box-sizing: border-box;
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        &__clear-button{
            width: 100%;
            border-radius: 50px;
            font-size: 1.5rem;
            border: none;
            background: rgb(7, 145, 99);
            transition: all 0.3s;
            align-self: bottom;
            padding:7px;
            &:hover{
                background: $hoverBc;
            }
        }
        &__form{
            display: flex;
            justify-content: space-between;
            &__input{
                background: none;
                color: inherit;
                border: none;
                padding: 10px;
                font: inherit;
                cursor: pointer;
                outline: inherit;
                width: 75%;
                border: none;
                background: #d8d8d8c0;
                font-size: 1.1rem;
                box-sizing: border-box;
                border-radius: 20px;
                &::placeholder{
                    color: black;
                }
            }
            &__add-button{
                width: 20%;
                border-radius: 50px;
                font-size: 1.5rem;
                border: none;
                background: rgb(7, 145, 99);
                transition: all 0.3s;
                &:hover{
                    background: $hoverBc;
                }
            }
        }
        &__list-container{
            display: flex;
            flex-direction: column;
            h2 {
                text-align: center;
                margin-bottom: 0;
                padding-bottom: 5px;
                font-size: 2rem;
                border-bottom: 4px solid rgb(7, 145, 99);
            }
            ul{
                padding-left: 0;
            }
            li{
                font-size: 1.3rem;
                display: flex;
                justify-content: space-between;
                align-items: center
            }
            &__button{
                text-decoration: none;
                font-size: 30px;
                display: flex;
                justify-content: center;
                align-items: center;
                background: transparent;
                border: none;
                &:hover{
                    color: $hoverBc;
                }
            }
        }
        


    }


</style>