<template>
    <div class="container">
        <h1>To do list</h1>
        <app-new-task @taskAdded="newTask"></app-new-task>
        <app-progress-bar :max-tasks="maxTasks" :tasksCount="tasks.length"></app-progress-bar>
        <app-task-grid :tasks="tasks" @gridTaskDeleted="taskDeleted" @gridTaskFinished="thisTaskFinished" @gridTaskUnfinished="thisTaskUnfinished" :class="{ 'finished':tasks.taskFinished }"></app-task-grid>
    </div>
</template>

<script>
    import TaskGrid from "./components/TaskGrid";
    import NewTask from  "./components/NewTask";
    import ProgressBar from "./components/ProgressBar";
    export default {
        data() {
            return {
                tasks: [{name: 'test task', taskFinished: false}],
                maxTasks: 50,
            }
        },
        components: {
            appTaskGrid: TaskGrid,
            appNewTask: NewTask,
            appProgressBar: ProgressBar,
        },
        methods: {
            newTask(task){
                if (this.tasks.length >= this.maxTasks){
                    return alert('Finish previous tasks first')
                }
                if (task !== ''){
                    this.tasks.push({name: task, taskFinished: false});
                }
            },
            taskDeleted(index){
                this.tasks.splice(index, 1);
            },
            thisTaskFinished(index){
                this.tasks[index].taskFinished = true;
            },
            thisTaskUnfinished(index){
                this.tasks[index].taskFinished = false;
                console.log(this.tasks[index].taskFinished)
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
