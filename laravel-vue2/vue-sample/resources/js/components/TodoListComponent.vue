<template>
    <div class="container">
        <div class="row justify-content-center">
            <form v-on:submit.prevent="addTodo" action="get">
                <input v-model="todo" />
                <input type="submit" val="追加" />
            </form>
            <ul v-for="item in list">
                {{
                    item
                }}
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "TodoListComponent",
    data() {
        return {
            todo: "",
            list: ["todo1", "todo2"]
        };
    },
    methods: {
        addTodo() {
            this.list.push(this.todo);
            this.todo = "";
        }
    }
};
</script>
