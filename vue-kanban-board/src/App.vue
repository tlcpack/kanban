<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col form-inline">
        <b-form-input
          id="input-2"
          v-model="newTask"
          required
          placeholder="Enter Task"
          @keyup.enter="add"
        ></b-form-input>
        <b-button @click="add" variant="primary" class="ml-3">Add</b-button>
      </div>
    </div>
    <div class="row mt-5">
      <div class="col-3">
        <div class="p-2 alert alert-secondary">
          <h3>Backlog</h3>
          <draggable class="list-group kanban-column" :list="arrBackLog" group="tasks">
            <div
              class="list-group-item"
              v-for="element in arrBackLog"
              :key="element.name"
            >{{ element.name }}</div>
          </draggable>
        </div>
      </div>
      <div class="col-3">
        <div class="p-2 alert alert-secondary">
          <h3>In progress</h3>
          <draggable class="list-group kanban-column" :list="arrInProgress" group="tasks">
            <div
              class="list-group-item"
              v-for="element in arrInProgress"
              :key="element.name"
            >{{ element.name }}</div>
          </draggable>
        </div>
      </div>
      <div class="col-3">
        <div class="p-2 alert alert-secondary">
          <h3>Testing</h3>
          <draggable class="list-group kanban-column" :list="arrTested" group="tasks">
            <div
              class="list-group-item"
              v-for="element in arrTested"
              :key="element.name"
            >{{ element.name }}</div>
          </draggable>
        </div>
      </div>
      <div class="col-3">
        <div class="p-2 alert alert-secondary">
          <h3>Done</h3>
          <draggable class="list-group kanban-column" :list="arrDone" group="tasks">
            <div
              class="list-group-item"
              v-for="element in arrDone"
              :key="element.name"
            >{{ element.name }}</div>
          </draggable>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable";

export default {
  name: "kanban-board",
  components: {
    draggable,
  },
  data() {
    return {
      newTask: "",
      arrBackLog: [
        { name: "Sign up page" },
        { name: "Test dashboard" },
        { name: "Styling" },
      ],
      arrInProgress: [],
      arrTested: [],
      arrDone: [],
    };
  },
  methods: {
    add: function () {
      if (this.newTask) {
        this.arrBackLog.push({ name: this.newTask });
        this.newTask = "";
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
