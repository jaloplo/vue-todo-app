<template>
    <div class="columns is-centered">
        <ul class="todo-list column is-full">

            <li v-for="todo in todos" :key="todo.id" class="todo-list-item columns is-centered">
                <div class="column is-2 has-text-centered">
                    <span v-if="todo.importance === 'high'" class="tag is-danger">High</span>
                    <span v-if="todo.importance === 'medium'" class="tag is-primary">Medium</span>
                    <span v-if="todo.importance === 'low'" class="tag is-info">Low</span>
                </div>
                <div class="column is-8">
                    <del v-if="todo.completed === true" class="is-size-6 has-text-grey-lighter">{{ todo.title }}</del>
                    <span v-if="todo.completed === false" class="is-size-6">{{ todo.title }}</span>
                </div>
                <div class="column is-1 has-text-centered">
                    <input type="checkbox" v-model="todo.completed" @click="$emit('completeTask', todo)" />
                </div>
                <div class="todo-item-delete column is-1 has-text-centered">
                    <a class="delete" @click="$emit('deleteTask', todo)"></a>
                </div>
            </li>

             <li class="todo-list-footer columns is-centered">
                 <div class="column is-12">
                    <div class="buttons is-centered">
                        <button class="button is-primary is-outlined" :disabled="areAllTasksCompleted" type="button" @click="$emit('markAllTasksAsCompleted')">Mark all as completed</button>
                        <button class="button is-primary is-outlined" :disabled="this.todos.filter(t => t.completed === true).length < 1" type="button" @click="$emit('clearCompletedTasks')">Clear completed</button>
                    </div>
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
        }
    }
}
</script>

<style lang="sass" scoped>
.todo-list
    margin-top: 20px

    .todo-item-delete
        visibility: hidden

    li
        border-bottom: solid 1px #00d1b2
        margin: 0
        padding: 0
    
    li:hover
        background-color: #00d1b2

        .todo-item-delete
            visibility: inherit
    
    li:first-child
        background-color: inherit
        border-left: 0
        padding: 0

    li:last-child
        background-color: inherit

    .todo-list-footer
        border-bottom: 0
</style>