<template>
    <div class="row">
        <app-task v-for="(task, index) in tasks" @deleteCurrentTask="gridTaskDeleted(index)" @finishCurrentTask="gridTaskFinished(index)" :class="{ 'finished': task.taskFinished }">{{ task.name }}</app-task>
    </div>
</template>

<script>
    import Task from './Task';
    export default {
        props: ['tasks'],
        components: {
            appTask: Task,
        },
        methods: {
            gridTaskDeleted(index){
                this.$emit('gridTaskDeleted', index);
            },
            gridTaskFinished(index){
                this.$emit('gridTaskFinished', index);
            }
        }
    }
</script>

<style scoped>
    .finished {
        text-decoration: line-through;
    }

</style>