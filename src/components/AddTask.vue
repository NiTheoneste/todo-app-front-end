<script>
    export default {
        data() {
            return {
                task: {
                    title: "",
                    date: "",
                    state: "new"
                }
            }
        },
        methods: {
            saveTask(){
                if (this.task.title.trim() == ""){
                    alert("Fill the title")
                }
                else{
                    this.$emit("taskEmited", this.task)
                }
                
            }
        }
    }
</script>
<template>
    <div>
        <h1>Add New Task</h1>
        <label>Title</label>
        <input v-model="task.title" type="text" placeholder="Enter a task title">
        <label>Date</label>
        <input v-model="task.date" type="date">
        <button @click="saveTask">Save</button>
    </div>
</template>
<style scoped></style>