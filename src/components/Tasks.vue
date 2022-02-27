<template>

  <div  :key="task.id"  v-for="task in tasks">
         <Task @delete-task="$emit('delete-task',task.id)" @handle-remi="$emit('handle-remi',task.id)"  :task="task"/>
       
    </div>
  
</template>

<script>
import Task from "./Task"

export default{
    name:"Tasks",
    props:{
        tasks:{
            type:Array,

        }

    },
    components:{
        Task,
     
    },
    emits:['delete-task','handle-remi'] //we should pass our customed event handler like this to the upper component
}

</script>

<style>


</style>
