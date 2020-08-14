<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
import draggable from 'vuedraggable';

export default {
  name: 'kanban-board',
  components: {
    draggable
  },
  data() {
    return {
      newTask: '',
      arrBackLog: [
        { name: 'Sign up page'},
        { name: 'Test dashboard'},
        { name: 'Styling'}
      ],
      arrInProgress: [],
      arrTested: [],
      arrDone: []
    };
  },
  methods: {
    add: function() {
      if (this.newTask) {
        this.arrBackLog.push({ name: this.newTask });
        this.newTask = '';
      }
    }
  }
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
