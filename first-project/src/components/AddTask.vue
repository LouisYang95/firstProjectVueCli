<template>
  <form @submit.prevent>
    <div class="form-group">
      <label>Task</label>
      <input type="text" id="formTask" class="form-control" placeholder="Enter Task" />
      <small class="form-text text-muted"
        >Add a task that you have to do.</small
      >
    </div>
    <div class="form-group">
      <label>Content</label>
      <input type="text" id="formContent" class="form-control" placeholder="Content to add" />
    </div>
    <button type="submit" class="btn btn-primary" @click="addTask()">Submit</button>
  </form>
  <div>
    <h1>{{task}}</h1>
  </div>
</template>

<script>
export default {
  name: "AddTask",
  data() {
    return {
      task: "",
      about: "",
    };
  },
  methods: {
    addTask() {
        this.task = document.getElementById("formTask").value;
        this.about = document.getElementById("formContent").value;
        localStorage.setItem("task", this.task);
        localStorage.setItem("about", this.about);
  },
}
}
</script>

<style scoped>
form {
  width: 30%;
  margin: 0 auto;
}
.form-group {
  margin-bottom: 1rem;
}
</style>
