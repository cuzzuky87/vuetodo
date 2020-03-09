<template>
  <div class="task">
    <table>
      <tr>
        <th>Task Name</th>
        <th>Status</th>
      </tr>
      <tr v-for="(task, index) in tasks" :key="index">
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
      console.log("test");
    }
  }
};
</script>
