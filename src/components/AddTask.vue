<script>
    export default {
        data() {
            return {
                btn:"save",
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
                    let task_obj = JSON.parse(JSON.stringify(this.task))
                    this.task.title=""
                    this.task.date = ""
                    if(this.taskProp==null){
                        this.$emit("createTaskEmited", task_obj)
                    }else{
                        this.$emit("modifyTaskEmited", task_obj)
                    }
                        
                }
                
            }
        },
        props: ["taskProp"],
        watch: {
            "taskProp":{
                deep: true,
                handler(new_value) {
                    console.log(new_value)
                    this.btn="modify"
                    this.task.title = new_value.title
                    this.task.date = new_value.date
                }
            }
        }
    }
</script>
<template>
    <div class="modal">
        <div class="modal-content">
            <h1>Add New Task</h1>
            <label>Title</label>
            <input v-model="task.title" type="text" placeholder="Enter a task title">
            <label>Date</label>
            <input v-model="task.date" type="date" >
            <button @click="saveTask">{{btn}}</button>
            <p>Prop: {{ taskProp }}</p>
        </div>
    </div>
</template>
<style scoped>
.modal {
  display: block;
  position: fixed;
  z-index: 1; 
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto; 
  background-color: rgba(0, 0, 0, 0.4); 
}

.modal-content {
  background-color: #fefefe;
  margin: 15% auto;
  padding: 20px;
  border: 1px solid #888;
  width: 80%;
  border-radius: 5px;
}
</style>