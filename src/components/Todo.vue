<template>
  <div class="container input-select-section">
    <div class="input-group">
      <div class="input-group mb-3 container">
        <div class="row">
          <div class="col input-section">
            <input
              v-model="todotext"
              type="text"
              class="form-control"
              placeholder="Please type your new todo..."
              aria-label="Recipient's username"
              aria-describedby="button-addon2"
            />
          </div>
          <div class="col-md-auto ml-0">
            <div class="input-group-append">
              <select
                v-model="todolistpriority"
                class="select-section"
              >
                <option v-for="priority in priorities" :key="priority">{{ priority }}</option>
              </select>
            </div>
          </div>
          <div class="col col-lg-2">
            <button type="button" class="btn btn-secondary button" @click="addNewTodo()">Add New Todo</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { eventBus } from "../main";
export default {
  data() {
    return {
      todotext: "",
      todolistpriority: "",
      priorities: ["Highest", "High", "Low"],
      priority : false
    };
  },
  methods: {
    addNewTodo: function() {
      if (this.todotext == "" || this.todolistpriority == "") {
        this.$swal(
          "Warning",
          "You need to type something or set the priority",
          "warning"
        );
      } else {
        if (this.todolistpriority == "Highest") {
          eventBus.$emit("todoAddedHighest", this.todotext);
          this.todotext = "";
          eventBus.$emit("todopriorityHighest", this.todolistpriority);
        } else if (this.todolistpriority == "High") {
          eventBus.$emit("todoAddedHigh", this.todotext);
          this.todotext = "";
          eventBus.$emit("todopriorityHigh", this.todolistpriority);
        } else {
          eventBus.$emit("todoAddedLow", this.todotext);
          this.todotext = "";
          eventBus.$emit("todopriorityLOw", this.todolistpriority);
        }
      }
    }
  }
};
</script>

<style scoped>
.input-section {
  width: 800px;
}

.select-section {
  color: black;
  background-color: #f1f1f1;
  height: 25px;
  margin-top: 2px;
  margin-bottom: 2px;
}

.form-control{
  height: 30px;
  background-color: #f1f1f1;
}
.button{
  height: 35px;
}
</style>