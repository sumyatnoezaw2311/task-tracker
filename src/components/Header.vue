<template>
    <header>
        <h1>{{ title }}</h1>
        <div class="buttonContainer">
            <Button @click="onClick()" :name="show ? 'Close' : 'Add Task'" :color="show ? 'red': 'lightseagreen'"></Button>
        </div>
    </header>
</template>

<script>
    import Button from './Button.vue'

    export default {
        name: 'task-header',
        props: {
            title: String
        },
        data() {
            return {
                show: false
            };
        },
        components: {
            Button
        },
        methods: {
            onClick() {
                this.$emit('toggle-show-add-task');
                this.show = !this.show;
            }
        }
    }
</script>

<style>
    .buttonContainer{
        width: fit-content;
    }
    header{
        width: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
    }
</style>
