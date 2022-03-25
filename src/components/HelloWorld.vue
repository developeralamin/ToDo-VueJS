<template>
  <div class="hello">
     <h1>VueJs todo App</h1>
     <div class="container col-md-5">

  
      <div class="input-group mb-3">
        <input type="text" 
         class="form-control"
         placeholder="Input here" 
         v-model="task" 
        >
        <button  type="submit" 
         class="btn btn-success"
         id="button-addon2" @click="addTask">Button</button>
      </div>

   

    <table class="table">
        <thead>
          <tr>
            <th scope="col">SL</th>
            <th scope="col">Task</th>
            <th scope="col">Status</th>
            <th scope="col">Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(task,index) in tasks" :key="index">
              <th scope="row">{{ index+1 }}</th>
              <td>{{ task.name }}</td>
              <td>{{ task.status }}</td>
              <td>
              <div @click="editTask(index)">
              <span  class="btn btn-success btn-sm">edit</span>
             </div>
              <div @click="deleteTask(index)">
              <span class="btn btn-danger btn-sm">delete</span>
             </div>
             
              </td>
          </tr>
         </tbody> 
    </table>



     </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return {
      task:'',
      editedTask:null,
      tasks:[
         {
          name: "Steal bananas from the supermarket.",
          status: "to-do",
         },
         {
          name: "Steal bananas from the supermarket.",
          status: "to-do",
         },
      ]
    }
  },
  methods: {

 // deleteTask
      deleteTask(index){
        this.tasks.splice(index,1);
      },
//edit task

    editTask(index){
      this.task = this.tasks[index].name
      this.editedTask = index
    },

    addTask(){
      // console.log(this.task)
      if(this.task.length === 0)return;

  if(this.editedTask !== null){
 /* We need to update the task */
    this.tasks[this.editedTask].name = this.task
    this.editedTask = null
  
 
    }

  else{
    /* We need to add new task */
    this.tasks.push({
          name: this.task,
          status: 'todo'
        })
  }
        
       this.task = null
    },



  },

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
