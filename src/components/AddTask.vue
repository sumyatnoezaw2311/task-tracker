<template>
    <form @submit="onSubmit" class="form-group">
        <div class="form-control">
            <label>Title : </label>
            <input name="text" v-model="text" type="text"/>
        </div>
        <div class="form-control">
            <label>Date :</label>
            <input name="day" v-model="day" type="date"/>
        </div>
        <div class="form-control-reminder">
            <label>Reminder :</label>
            <input name="reminder" v-model="reminder" type="checkbox">
        </div>
        <Button name="Save Task" color="lightseagreen"></Button>
    </form>
</template>

<script>
    import Button from './Button.vue'
    export default{
        name: 'AddTask',
        props:{
            tasks: Array
        },
        components:{
            Button
        },
        data(){
            return {
                text: '',
                day: '',
                reminder: false
            }
        },
        methods: {
            onSubmit(e){
                e.preventDefault()
                if(!this.text){
                    alert("Please add a text")
                    return
                }else if(!this.day){
                    alert("Please select a day")
                    return
                }
                
                const newTask = {
                    id: this.tasks ? this.tasks[this.tasks.length - 1].id + 1 : 1,
                    text: this.text,
                    day: this.day,
                    reminder: this.reminder
                }
                // console.log(newTask)
                this.$emit('add-new-task', newTask)

                this.text = ''
                this.day = ''
                this.reminder = false
            }
        }
    }
</script>

<style>
    .form-group{
        margin: 0px auto 15px auto;
        padding: 10px;
        width: 280px;
    }
    .form-control{
        margin-bottom: 10px;
        display: flex;
        flex-direction: column;
        align-items: flex-start;
    }
    .form-control input{
        width: 100%;
        min-height: 30px;
        outline-color: lightseagreen;
    }
    .form-control-reminder{
        display: flex;
        width: 200px;
        justify-content: space-between;
        margin: 15px auto;
    }
</style>