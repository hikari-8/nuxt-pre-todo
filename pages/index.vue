<template>
    <div class="app_container">
        <div class="button_container">
            <input v-model="newToDoName" />
            <button @click="addToDo" :disabled="!newToDoName">ToDoを追加</button>
        </div>

        <div class="todo_container">
            <div v-for="toDo of toDoItems" :key="toDo.createdAt">
                <div>{{ toDo.name }}</div>
            </div>
        </div>

    </div>
</template>


<script lang="ts">
import { Vue, Component } from "nuxt-property-decorator";
import { ToDoItem, TODO_STATUS } from "@/types";
import ToDoItemCard from "@/components/ToDoItemCard.vue";

@Component({
    components: {
        ToDoItemCard,
    },
})
export default class TopPage extends Vue {
    public message = "HELLO WORLD, welcome to STAGE2";
    public toDoItems: ToDoItem[] = [];
    public newToDoName ="";

    public addToDo() {
        if (this.newToDoName) {
            this.toDoItems.push({
                name: this.newToDoName,
                status: "PENDING",
                createdAT: new Date().getTime(),
        });
    }
        this.newToDoName = "";
    }
}
</script>


<style lang="stylus" scoped>
.app_container {
    .button_container {
        margin: 100px 0 60px;
        text-align: center;
        width: 100%;
    }
    .todo_container {
        text-align: center;
        width: 100%;
    }
}
</style>