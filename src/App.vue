<template>
  <div class="w-25 m-auto">
    <div class="container-fluid my-3 border rounded py-3">
      <div class="row my-1">
        <div class="col">
          <label class="form-label">Nieuwe taak:</label>
          <input class="form-control my-1" id="priority" v-model="priority" type="number" min="1" max="3" placeholder="prioriteit">
          <input class="form-control my-1" id="label" v-model="label" type="text" placeholder="label">
          <textarea class="form-control my-1" id="description" v-model="description" type="text" placeholder="omschrijving"></textarea>
        </div>
      </div>
      <div class="row my-1">
        <div class="col d-flex justify-content-end">
          <button class="btn btn-primary" @click="addTask()">Toevoegen</button>
        </div>
      </div>
    </div>
    <div class="container-fluid" v-show="tasks.length > 0">
      <ul class="row list-unstyled">
        <li v-for="(task, index) in tasks" :key="task.id" @click="removeTask(index)" class="col-12 my-2 p-2 border rounded">
          <div class="container">
            <div class="row">
              <h6 class="col-6">Prioriteit: {{ task.priority }}</h6>
              <p class="badge rounded-pill text-bg-info col-4 offset-2 p-2">{{ task.label }}</p>
              <p class="col">{{ task.description }}</p>
            </div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      description: "",
      priority: "",
      label: "",
      tasks: []
    }
  },
  methods: {
    addTask() {
      const newTask = {
        id: this.tasks.length + 1,
        description: this.description,
        priority: this.priority,
        label: this.label
      }
      this.tasks.push(newTask);

      this.description = "";
      this.priority = "";
      this.label = "";
    },
    removeTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>
<style lang="scss">
  
</style>