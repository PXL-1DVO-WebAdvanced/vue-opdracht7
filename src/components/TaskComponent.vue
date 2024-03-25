<template>
    <li class="col-12 my-2 p-2 border rounded">
        <div class="container">
            <div class="row">
                <input v-if="showPriority" type="number" v-model="newPriority" min="1" max="3" v-on:keydown.enter="changePriority()" class="col-6">
                <h6 v-else @click="toggleInput()" class="col-6">Prioriteit: {{ task.priority }}</h6>

                <p class="badge rounded-pill text-bg-info col-4 offset-2 p-2">{{ task.label }}</p>
                <p class="col">{{ task.description }}</p>
            </div>
        </div>
    </li>
</template>
<script>
export default {
    props: [
        'task'
    ],
    emits: [
        'changePriority'
    ],
    data() {
        return {
            newPriority: "",
            showPriority: false
        }
    },
    methods: {
        toggleInput() {
            this.showPriority = !this.showPriority;
        },
        changePriority() {
            this.$emit('changePriority', {id: this.task.id, newPriority: this.newPriority});
            this.newPriority = ""
            this.toggleInput();
        }
    }
}
</script>
<style scoped>

</style>
