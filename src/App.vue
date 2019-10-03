<template>
    <div class="container">
        <h1>To do list</h1>
        <app-new-task @taskAdded="newTask"></app-new-task>
        <app-task-grid :tasks="tasks" @gridTaskDeleted="taskDeleted" @gridTaskFinished="thisTaskFinished" :class="{ 'finished':tasks.taskFinished }"></app-task-grid>
    </div>
</template>

<script>
    import TaskGrid from "./components/TaskGrid";
    import NewTask from  "./components/NewTask"
    export default {
        data() {
            return {
                tasks: [{name: 'test task', taskFinished: false}],
                maxTasks: 15
            }
        },
        components: {
            appTaskGrid: TaskGrid,
            appNewTask: NewTask,
        },
        methods: {
            newTask(task){
                if (task !== ''){
                    this.tasks.push({name: task, taskFinished: false});
                }
            },
            taskDeleted(index){
                this.tasks.splice(index, 1);
            },
            thisTaskFinished(index){
                this.tasks[index].taskFinished = true;
                console.log(this.tasks[index].taskFinished);
            }
        }
    }
</script>

<style>
    h1 {
        text-align: center;
        margin-top: 100px;
       font-size: 40px;
    }
</style>
