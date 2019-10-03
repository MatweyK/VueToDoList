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

    // localStorage.clear();
    const presetValues = [{
            "name": "Wake up at 5am",
            "taskFinished": true },
        {
            "name": "Learn how to use Vue.js",
            "taskFinished": false },
        {
            "name": "Drink coffee",
            "taskFinished": false }];

    // Use localStorage
    const STORAGE_KEY = "todo-app";
    const tasksStorage = {
        fetch: function () {
            let tasks = JSON.parse(localStorage.getItem(STORAGE_KEY)) || presetValues;
            tasks.forEach(function (task, index) {
                task.id = index;
            });
            tasksStorage.uid = tasks.length;
            return tasks;
        },
        save: function (tasks) {
            localStorage.setItem(STORAGE_KEY, JSON.stringify(tasks));
        } };

    export default {
        data() {
            return {
                tasks: tasksStorage.fetch(),
                maxTasks: 50,
            }
        },
        watch: {
            tasks: {
                handler: function (tasks) {
                    tasksStorage.save(tasks);
                },
                deep: true
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
