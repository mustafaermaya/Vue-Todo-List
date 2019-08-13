<template>
  <div class="everything">
    <div class="container sss">
      <br>
      <br>
      <app-todo></app-todo>
    </div>
    <br>
    <br>
    <div class="container">
      <div class="row">
        <div class="col">
          <app-todo-highest></app-todo-highest>
          <br><br>
          <app-highest-complited></app-highest-complited>
        </div>
        <div class="col">
          <app-todo-high></app-todo-high>
          <br><br>
          <app-high-complited></app-high-complited>
        </div>
        <div class="col">
          <app-todo-low></app-todo-low>
          <br><br>
          <app-low-complited></app-low-complited>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from "../main";
import Todo from "./Todo";
import HighestTodo from "./HighestTodo";
import HightTodo from "./HighTodo";
import LowTodo from "./LowTodo";
import HighestComponentComplited from './HighestComponentComplited';
import HighComponentComplited from './HighComponentComplited';
import LowComponentComplited from './LowComponentComplited';
export default {
  data() {
    return {};
  },
  components: {
    appTodo: Todo,
    appTodoHighest: HighestTodo,
    appTodoHigh: HightTodo,
    appTodoLow: LowTodo,
    appHighestComplited : HighestComponentComplited,
    appHighComplited : HighComponentComplited,
    appLowComplited : LowComponentComplited
  }
};
</script>

<style scoped>
.everything{
  background-color: #ABB0FF;
}
</style>