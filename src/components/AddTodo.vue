<template>
    <div id="add-todo">
        <h3>Add Todo</h3>
        <form @submit="addTodo">
            <input type="text" placeholder="Make a new Todo" v-model="title" />
            <button type="submit">Add</button>
        </form>
    </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";

export default {
    name: "AddTodo",
    data() {
        return {
            title: "",
        };
    },
    methods: {
        addTodo(e) {
            // Don't send data to form
            e.preventDefault();

            const newTodo = {
                id: uuidv4(),
                title: this.title,
                completed: false,
            };

            this.title = "";

            // Send up to parent
            this.$emit("add-todo", newTodo);
        },
    },
};
</script>

<style scoped>
h3 {
    margin: 10px 0;
}
input {
    width: 250px;
}
#add-todo {
    border: 1px solid gray;
    text-align: center;
    width: 300px;
}
</style>
