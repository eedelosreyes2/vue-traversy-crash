<template>
    <div class="row">
        <div
            id="todo"
            :class="{ completed: todo.completed }"
            @click="todo.completed = !todo.completed"
        >
            {{ todo.title }}
        </div>
        <button @click="$emit('del-todo', todo.id)">X</button>
    </div>
</template>

<script>
export default {
    name: "Todo",
    props: ["todo"],
};
</script>

<style scoped>
button {
    height: 20px;
}
#todo {
    text-align: left;
}
.row {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    /* padding: 0 30px; */
}
.completed {
    text-decoration: line-through;
}
</style>
