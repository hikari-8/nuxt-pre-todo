<template>
    <div>
        <div>{{ name }}</div>
        <div>
            <button @click="changeStatus" :style="style">{{ status }}</button>
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
    }
</script>
