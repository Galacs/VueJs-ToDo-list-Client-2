<template>
    <div id="app">
      <div class="button-box">
        <p style="text-align: center;">
          <button v-on:click="addToDo()" title="Ajouter un element a votre To Do liste" type="button" class="btn btn-info btn-circle btn-xl">
            <svg class="bi bi-plus" viewBox="0 0 16 16" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
              <path fill-rule="evenodd" d="M8 3.5a.5.5 0 0 1 .5.5v4a.5.5 0 0 1-.5.5H4a.5.5 0 0 1 0-1h3.5V4a.5.5 0 0 1 .5-.5z"/>
              <path fill-rule="evenodd" d="M7.5 8a.5.5 0 0 1 .5-.5h4a.5.5 0 0 1 0 1H8.5V12a.5.5 0 0 1-1 0V8z"/>
            </svg>
          </button>
        <button v-on:click="ClearTodos()" type="button" title="Supprimer tout les elements de votre to do liste" class="btn btn-warning btn-circle btn-xl">
          <svg class="bi bi-x" viewBox="0 0 16 16" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
            <path fill-rule="evenodd" d="M11.854 4.146a.5.5 0 0 1 0 .708l-7 7a.5.5 0 0 1-.708-.708l7-7a.5.5 0 0 1 .708 0z"/>
            <path fill-rule="evenodd" d="M4.146 4.146a.5.5 0 0 0 0 .708l7 7a.5.5 0 0 0 .708-.708l-7-7a.5.5 0 0 0-.708 0z"/>
          </svg>
        </button>
      </p>
    </div>
      <div v-cloak>      
        <ol>
          <li v-bind:key="todo.id" v-for="todo in todos">
            <div class="flex-container">
              <p>{{ todo.text }}</p>
              <button v-on:click="DeleteToDo(todo)" style="padding: 0 0; align-self: flex-end; height: auto; width: 5%; min-width: 30px;" type="button" class="btn btn-warning btn-circle btn-lg">
                <svg class="bi bi-x" viewBox="0 0 16 16" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
                  <path fill-rule="evenodd" d="M11.854 4.146a.5.5 0 0 1 0 .708l-7 7a.5.5 0 0 1-.708-.708l7-7a.5.5 0 0 1 .708 0z"/>
                  <path fill-rule="evenodd" d="M4.146 4.146a.5.5 0 0 0 0 .708l7 7a.5.5 0 0 0 .708-.708l-7-7a.5.5 0 0 0-.708 0z"/>
                </svg>
              </button>
            </div>
          </li>
        </ol>
      </div>
  </div>
</template>

<script>
export default {
  name: 'todoList',
  data () {
    return {
      todos: [],
      id: 1
    }
  },
  methods: {
    DeleteToDo: function(todo){
      this.todos.splice(this.todos.indexOf(todo), 1);
      console.log(this.todos.length);
    },
    addToDo(){
      const todo = prompt("Tache a faire:");
      if(todo === '') return;
      this.todos.push({
        text: todo,
        id: this.id
      })
      this.id++;
      console.log(this.todos.length);
    },
    ClearTodos(){
      this.todos = []
      console.log(this.todos.length);
    },
    ManualaddToDo(name, number = 1){
      for (let i = 0; i < number; i++) {
        this.todos.push({
          text: name,
          id: this.id
        })
        this.id++;
      }
      console.log(this.todos.length);
    }    
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.btn-circle.btn-xl {
    width: 70px;
    height: 70px;
    padding: 10px 16px;
    border-radius: 35px;
    font-size: 24px;
    line-height: 1.33;
}

.btn-circle {
    width: 30px;
    height: 30px;
    padding: 6px 0px;
    border-radius: 15px;
    text-align: center;
    font-size: 12px;
    line-height: 1.42857;
}


* {margin: 0; padding: 0;}
 
div {
  margin: 20px;
}
 
ul {
  list-style-type: none;
  width: 500px;
}
 
h3 {
  font: bold 20px/1.5 Helvetica, Verdana, sans-serif;
}
 
li img {
  float: left;
  margin: 0 15px 0 0;
}
 
li p {
  /* font: 200 12px/1.5 Georgia, Times New Roman, serif; */
  font-size: 30px;
}
 
li {
  padding: 10px;
  overflow: auto;
}
 
li:hover {
  background: #eee;
  cursor: pointer;
}

.flex-container{
  display: flex;
  justify-content: space-between;
}
</style>
