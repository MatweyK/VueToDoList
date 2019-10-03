<template>
    <div class="col-sm-6 col-md-4 col-lg-3">
        <div class="card bg-light">
            <div class="card-body task">
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
    button {
        display: inline-block;
    }
    .card {
        margin: 10px;

    }
    .card-body {
        font-family: 'Roboto', sans-serif;
        font-size: 24px;
        color: dimgrey;
        cursor: pointer;

    }

    /*.finished {*/
    /*    text-decoration: line-through;*/
    /*}*/
    .finished .card-body{
        background-color: #ff9797;
    }
</style>