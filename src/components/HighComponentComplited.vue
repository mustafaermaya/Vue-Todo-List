<template>
  <div class="container f">
    <div v-if="!todoslistHighest.length || !todoprioritylistHighest.length">
      <h3 class="highp">High Complited</h3>
      <p>Nothing on the complited high ToDo list...</p>
    </div>
    <div v-else class="container">
      <h3 class="p">Complited High Todo List</h3>
      <ul>
        <li v-for="(todos , index) in todoslistHighest" :key="index" class="checked">
          {{ todos }}
          <span class="close" @click="removeTodo(index)">X</span>
        </li>
        <br />
      </ul>
    </div>
  </div>
</template>
 
 <script>
import { eventBus } from "../main";
import Todo from "./Todo";
export default {
  data() {
    return {
      todoslistHighest: [],
      todoprioritylistHighest: []
    };
  },
  methods: {
    removeTodo: function(index) {
      this.todoslistHighest.splice(index, 1);
      this.todoprioritylistHighest.splice(index, 1);
    }
  },
  created() {
    eventBus.$on("removedTodolistHigh", todocomplited => {
      this.todoslistHighest.push(todocomplited);
    });
    eventBus.$on("removedTodoListHighPriority", prioritycomplited => {
      this.todoprioritylistHighest.push(prioritycomplited);
    });
  }
};
</script>
 
 <style scoped>
* {
  box-sizing: border-box;
}

/* Remove margins and padding from the list */
ul {
  margin: 0;
  padding: 0;
}

/* Style the list items */
ul li {
  cursor: pointer;
  position: relative;
  padding: 10px 16px 12px 35px;
  text-align: center;
  align-items: center;
  list-style-type: none;
  background: #eee;
  font-size: 12px;
  transition: 0.2s;
  height: 35px;

  /* make the list items unselectable */
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Set all odd list items to a different color (zebra-stripes) */
ul li:nth-child(odd) {
  background: #fcd29e;
}

/* Darker background-color on hover */
ul li:hover {
  background: #fba335;
}

/* When clicked on, add a background color and strike out text */
ul li.checked {
  background: #3e545a;
  color: #fff;
  text-decoration: line-through;
}

/* Add a "checked" mark when clicked on */
ul li.checked::before {
  content: "";
  position: absolute;
  border-color: #fff;
  top: 10px;
  left: 16px;
}

/* Style the close button */
.close {
  position: absolute;
  font-size: 12px;
  right: 0;
  top: 0;
  padding: 12px 12px 12px 12px;
  color: yellow;
}

.close:hover {
  background-color: #f44336;
  color: white;
}

/* Style the header */
.header {
  background-color: #f44336;
  padding: 30px 40px;
  color: white;
  text-align: center;
}

/* Clear floats after the header */
.header:after {
  content: "";
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
  font-size: 16px;
}

/* Style the "Add" button */
.addBtn {
  padding: 10px;
  width: 25%;
  background: #d9d9d9;
  color: #555;
  float: left;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
  transition: 0.3s;
  border-radius: 0;
}

.addBtn:hover {
  background-color: #bbb;
}

.p {
  margin-left: 20px;
}

.highestcomp {
  margin-top: 10px;
}

.easy {
  position: absolute;
  font-size: 10px;
  right: 0;
  top: 0;
  padding: 12px 12px 12px 12px;
  margin-right: 261px;
  color: yellow;
}

</style>
