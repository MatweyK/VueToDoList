<template>
    <div class="row">
        <div class="col-12">
            <div class="progress">
                <div class="progress-bar" role="progressbar" aria-valuenow="0" aria-valuemin="0" aria-valuemax="100" :style="{ width: (tasksCount/maxTasks)*100 + '%' }">
                    {{ tasksCount }} / {{ maxTasks }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['tasksCount', 'maxTasks']
    }
</script>

<style scoped>

</style>