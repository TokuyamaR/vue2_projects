<template>
    <div class="container">
        <div class="row justify-content-center">
            <form v-on:submit.prevent="addTodo" action="get">
                <input v-model="todo" />
                <input type="submit" val="追加" />
            </form>
            <ul v-for="item in list" v-bind:key="item.id">
                <li v-on:click="doneTodo(item)">
                    <span>id: {{ item.id }} </span>
                    <span>status: {{ item.status }}</span>
                    <s v-if="item.status === 'done'">
                        {{ item.text }}
                    </s>
                    <span v-else>
                        {{ item.text }}
                    </span>
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: "TodoListComponent",
    data() {
        return {
            id: 1,
            todo: "",
            list: []
        };
    },
    methods: {
        addTodo() {
            this.list.push({
                id: this.id++,
                text: this.todo,
                status: "todo"
            });
            this.todo = "";
        },
        doneTodo(item) {
            if (item.status === "done") {
                item.status = "todo";
            } else {
                item.status = "done";
            }
        }
    }
};
</script>
