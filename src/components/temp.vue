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
import axios from "axios";

export default {
    name: "App",
    components: {
        // HelloWorld
        AddTodo,
        Todos,
    },
    data() {
        return {
            todos: [],
        };
    },
    methods: {
        addTodo(newTodo) {
            const { title, completed } = newTodo;
            axios
                .post("https://jsonplaceholder.typicode.com/todos", {
                    title,
                    completed,
                })
                .then((res) => (this.todos = [...this.todos, res.data]))
                .catch((err) => console.log(err));
        },
        deleteTodo(id) {
            axios
                .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
                .then(
                    () =>
                        (this.todos = [
                            ...this.todos.filter((todo) => todo.id !== id),
                        ])
                )
                .catch((err) => console.log(err));
        },
    },
    created() {
        axios
            .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
            .then((res) => (this.todos = res.data))
            .catch((err) => console.log(err));
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
