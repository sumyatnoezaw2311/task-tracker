<template>
    <button :style="{ background: color}" >{{ name }}</button>
</template>

<script>
    export default {
        name: 'task-button',
        props: {
            name: {
                type: String,
                default: "click me"
            },
            color: {
                type: String,
                default: 'blue'
            },
        }
    }
</script>

<style>
    button{
        color: #fff;
        height: fit-content;
        border-radius: 5px;
        border: 1px solid #fff;
        padding: 5px 10px;
        width: 100%;
    }
</style>