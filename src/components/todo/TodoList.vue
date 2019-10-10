<template>
    <div class="columns is-centered">
        <ul class="todo-list column is-full">
            <li class="todo-list-header columns is-centered">
                <div class="column is-three-quarters">
                    <span class="is-uppercase has-text-weight-semibold is-size-5">Description</span>
                </div>
                <div class="column is-one-quarter has-text-centered">
                    <input type="checkbox" v-model="areAllTasksCompleted" />
                </div>
            </li>
            <li v-for="todo in todos" :key="todo.id" class="todo-list-item columns is-centered">
                <div class="column is-three-quarters">
                    <span class="is-size-6">{{ todo.title }}</span>
                </div>
                <div class="column is-one-quarter has-text-centered">
                    <input type="checkbox" v-model="todo.completed" @click="$emit('completeTask', todo)" />
                </div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'TodoList',
    props: [ 'todos' ],
    computed: {
        areAllTasksCompleted: {
            get() {
                return this.todos.length === this.todos.filter(t => t.completed === true).length;
            },
            set() {
                this.$emit('completeAllTasks');
            }
        }
    }
}
</script>

<style lang="sass" scoped>
.todo-list
    margin-top: 20px

    li
        border-bottom: solid 1px #00d1b2
        margin: 0
        padding: 0
    
    li:first-child
        border-left: 0
        padding: 0
</style>