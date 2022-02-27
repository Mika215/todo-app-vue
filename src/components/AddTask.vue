<template>

    <form @submit="onSubmit" class="formcontainer">
    <div class="wrraper">
        <label for="text">Title</label>
        <input type="text" name="text" v-model=text placeholder="enter task" required>

    </div>
    <div class="wrraper">
        <label for="date">Date</label>
        <input type="text" name="date" v-model=date placeholder="enter due date and time" required>
  
    </div>
    <div class="wrraper checkbox-wrrap">
        <label for="reminder">Reminder</label>
        <input type="checkbox" checked v-model=reminder name="reminder">
    </div>
     <div class="wrraper" >
        <button type="submit" class="btn">Submit Task</button>
    </div>
    </form>


</template>

<script>
export default{
name:"AddTask",
props:{
 
},
data(){
    return{
        text:'',
        date:'',
        reminder:false,
    }
},
methods:{
    onSubmit(e){

e.preventDefault() 

const newTask={

    id:Date.now(),
    text:this.text,
    date:this.date,
    reminder:this.reminder,
    
} 
this.$emit('add-task',newTask)

    
      this.text = ''
      this.date = ''
      this.reminder = false
   
    }
    
 
}

}

</script>

<style scoped>

.formcontainer{
 
        margin-bottom: 40px;
    
}
.wrraper{
    margin: 20px 0;

}

.wrraper label{
     display: block;
  
}

.wrraper input{
 
    width: 100%;
    height: 30px;
    background: white;
    padding: 4px 5px;
    border-radius: 3px;
    border:1px solid lightseagreen;
    font-size: 17px;
}

.checkbox-wrrap{
  
display:flex;
align-items: center;
justify-content: space-between;
}

.checkbox-wrrap label{
  
flex: 1;

}


.checkbox-wrrap input{
  
flex: 2;
  height: 20px;
}



.btn {
    padding:6px 10px;
    width:120%;
    background-color: black;
    color:white;
    border:none;
    border-radius: 5px;
    font-weight: 600;
     font-size: 18px;
     margin-top: 8px;
     display: block;
  width: 100%;
}
.btn:active{
 transform: scale(1.03);
}


</style>