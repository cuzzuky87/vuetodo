<template>
  <div class="InputTask">
    <form v-on:submit.prevent="addtask(taskname)">
      <input type="text" v-model="taskname" placeholder="Input new Task" />
      <button v-on:click.prevent="addtask(taskname)">Submit</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "InputTask",
  data() {
    return {
      taskname: ""
    };
  },
  methods: {
    addtask: function(msg) {
      this.$emit("child-event", msg);
      this.taskname = "";
    }
  }
};
</script>

<style scoped>
.input {
  width: 130pt;
  height: 30pt;
}
.button {
  display: block;
  position: relative;
  margin: 0 auto;
  width: 70pt;
  border: solid 1px silver;
  border-radius: 0.5rem 1.5rem;
  padding: 0.5rem 1.5rem;
  margin-top: 1rem;
  text-decoration: none;
}
</style>
