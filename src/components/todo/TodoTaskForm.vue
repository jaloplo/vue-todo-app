<template>
    <div class="todo-form columns is-centered">
        <div class="column is-three-quarters">
            <div class="field">
                <div class="control">
                    <input class="input" type="text" placeholder="add a new task" v-model="title" />
                </div>
            </div>
        </div>
        <div class="column is-one-quarter has-text-centered">
            <div class="control">
                <button class="button is-primary" type="button" @click="addTask">Add</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'TodoTaskForm',
    data() {
        return {
            title: ''
        };
    },
    methods: {
        addTask() {
            this.$emit('new-task', this.title);
            this.title = '';
        }
    }
}
</script>