<template>
  <div class="task">
    <table>
      <tr>
        <th></th>
        <th>Task Name</th>
        <th>Status</th>
      </tr>
      <tr v-for="(task, index) in tasks" :key="index">
        <td>
          <button @click="clickDelete(task.name)">Delete</button>
        </td>
        <td>{{ task.name }}</td>
        <td v-if="task.flag">
          <button @click="click(task.name)">Done</button>
        </td>
        <td v-else>
          <button @click="click(task.name)">Not Yet</button>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  name: "TaskView",
  props: {
    tasks: Array
  },
  methods: {
    click: function(msg) {
      this.$emit("child-event", msg);
    },
    clickDelete: function(taskName) {
      this.$emit("delete-event", taskName);
      console.log("taskName" + taskName);
    }
  }
};
</script>
