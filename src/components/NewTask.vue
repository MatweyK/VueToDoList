<template>
    <div class="row">
        <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
            <form>
                <label>Add Task</label>
                <input type="text" class="form-control" v-model="task">
            </form>

        </div>
        <div class="col-sm-8 col-sm-offset-2 col-xs-12 col-md-6 col-md-offset-3 form-group">
           <button class="btn btn-primary" @click.prevent="createNew">Add Task</button>

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
            createNew(){
                this.$emit('taskAdded', this.task);
                this.task = '';
            }
        }
    }
</script>

<style scoped>
    .form-control {
        height: 50px;
        font-size: 24px;
    }
</style>