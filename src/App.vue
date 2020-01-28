<template>
  <div id="app">
    <InputTask v-on:child-event="TaskAdded" />
    <taskView v-bind:tasks="tasks" v-on:child-event="TaskFinished" />
  </div>
</template>

<script>
import TaskView from "./components/TaskView";
import InputTask from "./components/InputTask";

export default {
  name: "App",
  components: {
    TaskView,
    InputTask
  },
  data() {
    return {
      tasks: [
        { name: "no1", flag: "false" },
        { name: "no2", flag: "true" }
      ]
    };
  },
  methods: {
    TaskFinished: function(msg) {
      this.tasks.forEach(value => {
        if (value.name === msg) {
          if (value.flag === true) {
            value.flag = false;
          } else if (value.flag === false) {
            value.flag = true;
          }
        }
      });
    },
    TaskAdded: function(msg) {
      //console.log(msg);
      this.tasks.push({
        name: msg,
        flag: false
      });
    }
  }
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
