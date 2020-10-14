<template>
    <div id="todos">
        <h3>Todos</h3>
        <Todo
            v-for="todo in todos"
            :key="todo.id"
            :todo="todo"
            @del-todo="$emit('del-todo', todo.id)"
        />
        <div v-if="!todos || todos.length === 0" style="padding: 10px 0">
            There are no todos!
        </div>
    </div>
</template>

<script>
import Todo from "./Todo";

export default {
    name: "Todos",
    components: {
        Todo,
    },
    props: ["todos"],
};
</script>

<style scoped>
h3 {
    margin: 10px 0;
}
#todos {
    border: 1px solid gray;
    padding-bottom: 10px;
    text-align: center;
    width: 300px;
}
</style>
