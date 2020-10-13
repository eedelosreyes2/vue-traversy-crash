<template>
    <div id="app">
        <AddTodo @add-todo="addTodo" />
        <Todos :todos="todos" @del-todo="deleteTodo" />
    </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import AddTodo from "./components/AddTodo";
import Todos from "./components/Todos";

export default {
    name: "App",
    components: {
        // HelloWorld
        AddTodo,
        Todos,
    },
    data() {
        return {
            todos: [
                {
                    id: 0,
                    title: "Clean room",
                    completed: false,
                },
                {
                    id: 1,
                    title: "Wash dishes",
                    completed: false,
                },
                {
                    id: 2,
                    title: "Take out trash",
                    completed: false,
                },
            ],
        };
    },
    methods: {
        addTodo(newTodo) {
            this.todos = [...this.todos, newTodo];
        },
        deleteTodo(id) {
            this.todos = [...this.todos.filter((todo) => todo.id !== id)];
        },
    },
};
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;

    display: flex;
    flex-direction: column;
    align-items: center;
}
</style>
