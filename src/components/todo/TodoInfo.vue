<template>
    <div class="columns is-centered todo-info">
        <div class="column is-full">
            <div class="content">
                <div>Total tasks: {{ todos.length}}</div>
                <div>Completed tasks: {{ completedTodos.length }}</div>
            </div>
            <progress class="progress is-primary" :value="completedTodos.length" :max="todos.length" />
        </div>
    </div>
</template>

<script>
export default {
    name: 'TodoInfo',
    props: [ 'todos' ],
    computed: {
        completedTodos() {
            return this.todos.filter(t => t.completed === true);
        }
    }
}
</script>