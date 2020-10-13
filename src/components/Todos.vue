<template>
    <div id="todos">
        <h3>Todos</h3>
        <Todo
            v-for="todo in todos"
            :key="todo.id"
            :todo="todo"
            @del-todo="$emit('del-todo', todo.id)"
        />
    </div>
</template>

<script>
import Todo from "./Todo";

export default {
    name: "Todos",
    components: {
        Todo,
    },
    props: {
        todos: {
            type: Array,
            required: false,
            default: () => {
                return ["peep"];
            },
        },
    },
};
</script>

<style scoped>
h3 {
    margin: 10px 0 0 0;
}
#todos {
    border: 1px solid gray;
    text-align: center;
    width: 300px;
}
</style>
