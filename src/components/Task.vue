<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[taskContainer, task.reminder ? 'reminder' : '']">
        <div>
            <h4>{{ task.text }}</h4>
            <small>Date : {{ task.day }}</small>
        </div>
        <i @click="$emit('delete-task',task.id)" class="fas fa-times"></i>
    </div>    
</template>

<script>
    export default {
        name: "TaskItem",
        props: {
            task: Object
        },
        data() {
            return {
                taskContainer: "taskContainer"
            };
        },
    }
</script>

<style>
    .taskContainer{
        border-radius: 5px;
        padding: 5px 15px;
        margin-bottom: 5px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        border: 1px solid green;
        cursor: pointer;
    }
    .taskContainer small, h4{
        margin: 0px;
    }
    .taskContainer i{
        color: red;
        cursor: pointer;
    }
    .reminder{
        border-left: 5px solid green;
    }
    .taskContainer div{
        display: flex;
        flex-direction: column;
        align-items: self-start;
    }
</style>
