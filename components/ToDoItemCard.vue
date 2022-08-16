<template>
    <div class="todo_container">
        <div class="name">{{ name }}</div>
        <div class="button_status">
            <button @click="changeStatus" :style="style">{{ status }}</button>
        </div>
        <div class="button_remove">
            <button @click="removeItem">✖️</button>
        </div>
    </div>
</template>

<script lang="ts">
import { Component, Vue, Prop } from "nuxt-property-decorator";
import { ToDoItem } from "~/types";

@Component({})
    export default class ToDoItemCard extends Vue {
        @Prop({ required: true }) public toDoItem!: ToDoItem;

        public get name(): string {
            return this.toDoItem.name;
        }
        public get status(): string {
            switch (this.toDoItem.status) {
                case "PENDING":
                    return "未着手";
                case "DOING":
                    return "着手";
                case "DONE":
                    return "完了";
            }
        }
        public get style() {
            switch(this.toDoItem.status) {
                case "PENDING":
                    return { backgroundColor: "red", color: "white" };
                case "DOING":
                        return { backgroundColor: "green", color: "white"};
                case "DONE":
                    return { backgroundColor: "blue", color: "white"};
            }
        }

        public changeStatus() {
            switch (this.toDoItem.status) {
                case "PENDING":
                    this.toDoItem.status ="DOING";
                    break;
                case "DOING":
                    this.toDoItem.status ="DONE";
                    break;
                case "DONE":
                    this.toDoItem.status ="PENDING";
                    break;
            }
        }
        public removeItem() {
            this.$emit("remove");
        }
    }
</script>
