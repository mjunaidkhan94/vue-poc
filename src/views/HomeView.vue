<script setup lang="ts"></script>

<template>
  <div id="myDIV" class="header">
    <h2>My To Do List</h2>
    <input v-model="todoItem" type="text" id="myInput" placeholder="Title..." />
    <button class="addBtn" @click="addTodo()">Add</button>
  </div>


  <ul id="myUL">
    <li @click="todo.isChecked=!todo.isChecked" :class="{'checked': todo.isChecked}" v-for="todo in todoList">
      <span>{{ todo.content }}</span>
      <button v-if="!todo.isChecked" class="deleteBtn" @click.stop="deleteTodo(todo)">Delete</button>
      <!-- <span @click.stop="deleteTodo(todo)" class="delete-icon">✖</span> -->
    </li>
  </ul>
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
      count: 0,
      todoItem: '',
      todoList: [
        { id: 1, content: 'Send meeting invitation email to client', isChecked: false },
        { id: 2, content: 'Push my code to git repo', isChecked: true }
      ],
    }
  },
  methods: {
    addTodo(){
      this.todoList.push({
        id: this.todoList.length,
        content: this.todoItem,
        isChecked: false,
      });
      this.todoItem = "";
    },
    deleteTodo(todo){
      const index = this.todoList.findIndex((x)=> x==todo);
      this.todoList.splice(index, 1);
    },
  }
}
</script>

<style>
/* Include the padding and border in an element's total width and height */
* {
  font-size: 40px;
  box-sizing: border-box;
}

/* Remove margins and padding from the list */
ul {
  margin: 0;
  padding: 0;
}

/* Style the list items */
ul li {
  display: flex;
  justify-content: space-between;
  cursor: pointer;
  position: relative;
  padding: 12px 8px 12px 40px;
  background: #eee;
  font-size: 30px;
  transition: 0.2s;

  /* make the list items unselectable */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Set all odd list items to a different color (zebra-stripes) */
ul li:nth-child(odd) {
  background: #f9f9f9;
}

/* Darker background-color on hover */
ul li:hover {
  background: #ddd;
}

/* When clicked on, add a background color and strike out text */
ul li.checked {
  background: #888;
  color: #fff;
  text-decoration: line-through;
}

/* Add a "checked" mark when clicked on */
ul li.checked::before {
  content: '';
  position: absolute;
  border-color: #fff;
  border-style: solid;
  border-width: 0 2px 2px 0;
  top: 10px;
  left: 16px;
  transform: rotate(45deg);
  height: 15px;
  width: 7px;
}

/* Style the close button */
.close {
  position: absolute;
  right: 0;
  top: 0;
  padding: 12px 16px 12px 16px;
}

.close:hover {
  background-color: #033572;
  color: white;
}

/* Style the header */
.header {
  background-color: #033572;
  padding: 30px 40px;
  color: white;
  text-align: center;
}

/* Clear floats after the header */
.header:after {
  content: '';
  display: table;
  clear: both;
}

/* Style the input */
input {
  margin: 0;
  border: none;
  border-radius: 0;
  width: 75%;
  padding: 10px;
  float: left;
  font-size: 30px;
}

/* Style the "Add" button */
.addBtn {
  height: 56px;
  width: 25%;
  background: #d9d9d9;
  color: #555;
  float: left;
  text-align: center;
  font-size: 30px;
  cursor: pointer;
  transition: 0.3s;
  border-radius: 0;
}

.addBtn:hover {
  background-color: #bbb;
}

.deleteBtn {
  height: 56px;
  width: 25%;
  background: rgb(221, 0, 0);
  color: white;
  float: left;
  text-align: center;
  font-size: 30px;
  cursor: pointer;
  transition: 0.3s;
  border-radius: 0;
}


/* Add styles for the delete icon */
.delete-icon {
  cursor: pointer;
  margin-left: 10px; 
  color: red; 
}

/* Add a hover effect to the delete icon */
.delete-icon:hover {
  transform: scale(1.1);
}

</style>
