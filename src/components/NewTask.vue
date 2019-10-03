<template>
    <div class="row">
        <div class="col-12 addTaskFrom">
            <form action="" @submit="createNew">
                <label class="col-form-label">Add new Task</label>
                <input type="text" class="form-control-sm" v-model="task">
            </form>
            <button class="btn btn-primary addTask" @click="createNew" >Add Task</button>
        </div>

    </div>
</template>

<script>

    export default {
        data(){
            return {
                task: '',
            };
        },
        methods: {
            createNew(event){
                event.preventDefault();
                this.$emit('taskAdded', this.task);
                this.task = '';
            }
        }
    }
</script>

<style scoped>
    .col-form-label {
        display: block;
    }
    .form-control-sm {
        height: 50px;
        font-size: 24px;
    }
    .addTaskFrom {
        text-align: center;
    }
    .addTask {
        margin: 20px 0;
    }
</style>