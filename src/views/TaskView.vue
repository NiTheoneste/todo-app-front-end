<template>
    <div>
        <h1>TASK</h1>
        <ol>
            <li v-for="new_task, i in new_tasks">
                {{ i+1 }}
                Title: {{ new_task.title }}
                Date: {{ new_task.date }}
                State: {{ new_task.state }}
            </li>
        </ol>
        <AddTask @taskEmited="appendTask"/>
    </div>
</template>
<script>
import AddTask from '@/components/AddTask.vue';
export default {
    mounted() {
        console.log("Task is mounted")
    },
    data () {
        return {
            new_tasks : [
                {title: "Learn Vuejs", date: "10/02/2024", state: "new"},
                {title: "Learn Vuejs", date: "10/02/2024", state: "new"},
                {title: "Learn Vuejs", date: "10/02/2024", state: "new"}
            ],
            onprogress_tasks: [],
            completed_tasks: []
        }
    },
    components: {AddTask},
    methods: {
        appendTask(e){
            this.new_tasks.push(e)
            console.log(e)
        }
    }
}
</script>
<style scoped>
    h1 {
        color: red;
    }
</style>