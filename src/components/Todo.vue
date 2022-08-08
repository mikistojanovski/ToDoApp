<template>
  <div class="app">
    <div class="kkk">
      <header>
        <b class="naslov">TO DO LIST</b>
        <b-dropdown v-if="!(tasks.length==10)" id="burger" text="Add Task">

          <b-form-input>
            <input v-model="name" placeholder="Text" />
          </b-form-input>
          <select v-model="color">
            <option disabled value="">Color</option>
            <option>Red</option>
            <option>Blue</option>
            <option>Green</option>
          </select>
          <b-dropdown-item>
            <button @click="submitTask" class="btn btn-warning rounded-0">Add</button>
          </b-dropdown-item>
        </b-dropdown>
      </header>
    </div>
    <hr>

    <table class="table table-bordered ">

      <tbody>
        <tr v-for="(task,index) in tasks" :key="index">
          <div v-bind:style="{backgroundColor:task.color}">
            <td>{{task.name}}</td>
          </div>
          <td v-bind:style="{backgroundColor:task.color}">
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
  }

  ,
  data() {
    return {
      task: '',
      name: '',
      color: '',
      tasks: [
        {
          name: 'homearokme',
          color: 'blue'
        }
      ]
    }
  },
  methods: {
    submitTask() {
      if (this.name.length === 0) return;
      this.tasks.push({
        name: this.name,
        color: this.color
      });
      this.task = '';    
    },
    deleteTask(index) {
      this.tasks.splice(index, 1);
    }
  }
  };
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
*{
margin:0;
padding:0;
box-sizing:border-box;
}
.dropd{
  background-color: #222;
}
.burger{
  float:right;
  margin-right: 0;
  margin-left:auto;
  display:block;
}
.naslov{
  align-content: center;
}
.kkk{
background-color:#222;
text-align: center;
color:white;
}
.table {
  margin-top: 5%;
  width:75%;
  margin-left:auto;
  margin-right:auto;
}
</style>
