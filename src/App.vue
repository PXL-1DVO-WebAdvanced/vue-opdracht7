<template>
  <div class="w-25 m-auto">
    <form class="container-fluid my-3 border rounded py-3" @submit.prevent="addTask()">
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
          <input type="submit" class="btn btn-primary" value="Toevoegen">
        </div>
      </div>
    </form>
    <div class="container-fluid" v-show="tasks.length > 0">
      <ul class="row list-unstyled">
        <TaskComponent v-for="task in tasks" 
          :key="task.id" 
          :task="task"
          @changePriority="changeTaskPriority" />
      </ul>
    </div>
  </div>
</template>
<script>
import TaskComponent from './components/TaskComponent.vue';
export default {
  components: {
    TaskComponent
  },
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
    },
    changeTaskPriority(object) {
      let task = this.tasks.find(task => task.id = object.id);
      if (task) {
        task.priority = object.newPriority
      }
    }
  }
}
</script>
<style lang="scss">
  
</style>