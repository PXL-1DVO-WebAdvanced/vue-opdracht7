<template>
    <li class="col-12 my-2 p-2 border rounded">
        <div class="container">
            <div class="row">
                <h6 class="col-6">Prioriteit: {{ priority }}</h6>
                <p class="badge rounded-pill text-bg-info col-4 offset-2 p-2">{{ label }}</p>
                <p class="col">{{ description }}</p>
            </div>
        </div>
    </li>
</template>
<script>
export default {
    props: [
        'description',
        'priority',
        'label'
    ]
}
</script>
<style scoped>
    .task {
        background-color: red;
    }
</style>
