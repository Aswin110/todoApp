<template>
  <div class="container">
    <h2 class="text-center mt-5">My Vue Todo App</h2> 
    <!--input-->
    <div class="d-flex">
      <input v-model="task" type="text" placeholder="enter task " class="form-control">
      <button @click="submitTask" class="btn btn-warning rounded-0">SUBMIT</button>
    </div>

    <!--task table-->
    <table class="table table-bordered mt-5">
      <thead>
        <tr>
          <th scope="col">task</th>
          <th scope="col" class="text-center">status</th>
          <th scope="col" class="text-center">#</th>
          <th scope="col" class="text-center">#</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(task, index) in tasks" :key="index" >
          <td>
            <span :class="{'Finished':task.status==='Finished'}">{{ task.name }}</span>
          </td>
          <td class="text-center" style="width: 120px;">
            <span @click="changeStatus(index)" class="pointer"
            :class="{'text-danger':task.status==='To-do',
            'text-warning':task.status==='In-progress',
            'text-success':task.status==='Finished'}"
            >
              {{ task.status }}
            </span>
          </td>
          <td>
            <div class="text-center" @click="editTask(index)">
              <span class="fa fa-pen"></span>
            </div>
          </td>
          <td>
            <div class="text-center" @click="deleteTask(index)">
              <span class="fa fa-trash"></span>
            </div>
          </td>
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
  export default {
  name: 'HelloWorld',
    props: {
      msg: String
    },


    data(){
      return{
        task: '',
        editedTask:null,
        availableStatuses:['To-do','In-progress','Finished'],
        tasks:[
          {
            name: 'New task',
            status: 'To-do'
          },
          {
            name: 'workout for 30min'
            ,status:'Finished'
          }
        ]
      }
    },
    methods :{
      submitTask(){
        if(this.task.length === 0)return;
        if(this.editedTask===null){
          this.tasks.push({
              name: this.task,
              status: 'to-do'
          });
        }else{
          this.tasks[this.editedTask].name=this.task;//this task value will be saved in the respective tasks name
          this.editedTask=null;
        }

       this.task='' //to clear the search box after pressing submit
        console.log(this.task)
      },
      deleteTask(index){
        this.tasks.splice(index,1)
      },
      editTask(index){
      this.task=this.tasks[index].name; //this shows the selected field in input bar
      this.editedTask=index;
      },
      changeStatus(index){
        let newIndex =this.availableStatuses.indexOf(this.tasks[index].status);
        if(++newIndex>2)newIndex=0;
        this.tasks[index].status=this.availableStatuses[newIndex];
      },
    }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.pointer{
  cursor: pointer;
}
.Finished{
  text-decoration: line-through;
}
</style>
