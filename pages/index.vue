<template>
    <div class="app_container">
        <div class="message">{{ message }}</div>
    </div>
</template>
<script lang="ts">
import { Vue, Component } from "nuxt-property-decorator";

@Component({})
export default class TopPage extends Vue {
    public message = "HELLO WORLD, welcome to STAGE2";
}
</script>
<style lang="stylus" scoped>
.app_container {
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;

    .message {
        font-size: 40px;
        text-align: center;
        font-weight: bold;
    }
}
</style>