<template>
    <div class="row">
        <app-task v-for="(task, index) in tasks" @deleteCurrentTask="gridTaskDeleted(index)" @finishCurrentTask="gridTaskFinished(index)" :class="{ 'finished': task.taskFinished }">{{index +1}}. {{ task.name }}
            <div><button class="btn btn-primary" v-if="task.taskFinished" @click="unfinishCurrentTask(index)">Undone</button></div>
        </app-task>
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
            },
            unfinishCurrentTask(index){
                this.$emit('gridTaskUnfinished', index);
            }
        }
    }
</script>

<style scoped>
    .row {
        align-items: center;
    }
</style>