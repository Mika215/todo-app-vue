<template>
<div class="container">

 
   <Header @btn-click="setShowAddTask" title="Todo List"   :showAddTask="showAddTask" />
   <div v-show="showAddTask">
  <AddTask  @add-task="addTask"/>
   </div>
 
    <div class="taskcon">
      <Tasks @delete-task="deleteTask" @handle-remi="setReminder"  :tasks="tasks"/>
    </div>
  
   

 
</div>

</template>

<script>

import Header from "./components/Header"
import Tasks from "./components/Tasks"
import AddTask from "./components/AddTask"

export default {
  name: 'App',
  components: {
   Header,
   Tasks,
   AddTask,
  },
  data(){
    return{
      tasks:[],
      showAddTask:false,
       
    }
  },

  async created(){
    this.tasks= await this.getAllTasks()



},
  methods:{


setShowAddTask(){
  this.showAddTask=!this.showAddTask

},
//!Adding New Task
async addTask(newTask){


  const res= await fetch("api/tasks",{
    method:"POST",
    headers:{
      "Content-type":"application/json"
    },
   body:JSON.stringify(newTask)
  })
  const data=await res.json()

  this.tasks=[...this.tasks,data]
},
//!Deleting a task with id
   async deleteTask(taskId){
     if(confirm("Are you sure\nyou want to delete this task?")){

 const res= await fetch(`api/tasks/${taskId}`,{
 method:"DELETE"
 },)

  res.status===200 ?
  (this.tasks=this.tasks.filter((task)=>task.id!==taskId)):
  alert(`Error while deleteing task with Id No:${taskId}`)

    
     }
    },

    //!Updating reminder of a single task with id
   async setReminder(taskId){
const task2BUpdated= await this.getAllTasks(taskId)
const updatedTask= {...task2BUpdated,reminder:!task2BUpdated.reminder }


const res= await fetch(`api/tasks/${taskId}`,{
       method:"PUT",
         headers:{
      "Content-type":"application/json"
    },
    body:JSON.stringify(updatedTask)
     })
     
const data= await res.json()
      this.tasks=this.tasks.map((task)=>task.id===taskId?
      {...task,reminder:data.reminder}:task)

    },
    //!GET All Tasks
    async  getAllTasks(){
      const res= await fetch("api/tasks");
      const data= await res.json()
      return data
    },

      //GET single Task by id
    async  getSingleTask(id){
      const res= await fetch(`api/tasks${id}`);
      const data= await res.json()
      return data
    }
     
     
    
  }
 
}
</script>

<style>
#app {


max-width: 410px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 10px;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  
}





</style>
