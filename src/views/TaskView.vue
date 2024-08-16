<template>
    <div>
        <h1>TASK</h1>
        <button @click="add_task_shown=!add_task_shown">Add Task</button>
        <ol>
            <li v-for="new_task, i in new_tasks">
                {{ i }}
                Title: {{ new_task.title }}
                Date: {{ new_task.date }}
                State: {{ new_task.state }}
                <button @click="openEditTask(new_task, i)">Edit</button>
            </li>
        </ol>
        <AddTask
            v-if="add_task_shown"
            @createTaskEmited="createTask"
            :taskProp = "task_obj"
            @modifyTaskEmited="modifyTask"
        />
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
                {title: "Learn Vuejs", date: "2024-08-20", state: "new"},
                {title: "Learn Vuejs", date: "2024-03-10", state: "new"},
                {title: "Learn Vuejs", date: "2024-01-03", state: "new"}
            ],
            onprogress_tasks: [],
            completed_tasks: [],
            task_obj: null,
            index : null,
            add_task_shown:false
        }
    },
    components: {AddTask},
    methods: {
        createTask(e){
            this.new_tasks.push(e)
            this.add_task_shown=false
        },
        modifyTask(e){
            this.new_tasks[this.index] = e
            this.task_obj = null
            this.add_task_shown=false

        },
        openEditTask(task,idx){
            this.index = idx
            this.task_obj=task
            this.add_task_shown=true
        }
    }
}
</script>
<style scoped>
    h1 {
        color: red;
    }
</style>