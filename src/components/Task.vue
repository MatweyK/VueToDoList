<template>
    <div class="col-sm-6 col-md-4 col-lg-3">
        <div class="panel panel-default">
            <div class="panel-body task">
                <slot></slot>
                <div class="controls">
                    <button class="btn btn-success" @click="finishTask">Finish</button>
                    <button class="btn btn-danger" @click="deleteTask">Remove</button>
                </div>

            </div>
        </div>
    </div>
</template>

<script>
    export default {
        methods: {
            deleteTask(){
                this.$emit('deleteCurrentTask');
            },
            finishTask(){
                this.$emit('finishCurrentTask');
            },
        }
    }
</script>

<style scoped>
    .panel-body {
        font-family: 'Roboto', sans-serif;
        font-size: 24px;
        color: dimgrey;
    }
    .task {
        cursor: pointer;
    }
    .task:hover {
        background-color: gainsboro;
    }
</style>