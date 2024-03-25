<template>
  <div class="w-25 m-auto">
    <div class="container-fluid my-3 border rounded py-3">
      <div class="row my-1">
        <div class="col">
          <label class="form-label" for="taak">Nieuwe taak:</label>
          <input class="form-control" id="taak" v-model="newTask" type="text">
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
        <li v-for="(task, index) in tasks" v-bind:key="task" @click="removeTask(index)" class="my-2 p-3 border rounded">{{ task }}</li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: []
    }
  },
  methods: {
    addTask() {
      this.tasks.push(this.newTask);
    },
    removeTask(index) {
      this.tasks.splice(index, 1)
    }
  }
}
</script>
<style lang="scss">
  
</style>