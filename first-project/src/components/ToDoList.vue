<template>
  <div class="container">
    <div>
      <h1>ToDo List</h1>
    </div>
    <div>
      <table class="table table-dark">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">Task</th>
            <th scope="col">What's about</th>
            <th scope="col">Status</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">1</th>
            <td>{{task}}</td>
            <td>{{about}}</td>
          </tr>
          <tr>
            <th scope="row">2</th>
            
          </tr>
          <tr>
            <th scope="row">3</th>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDoList",
  data() {
    return {
      task: "",
      about: "",
    };
  },
  methods: {
    getTask() {
      this.task = localStorage.getItem("task");
      this.about = localStorage.getItem("about");
    },
  },
  mounted() {
    this.getTask();
  },
};
</script>

<style scoped></style>
