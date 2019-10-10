<template>
    <div class="columns is-centered todo-info">
        <ul class="column is-full">
            <li class="columns">
                <div class="column is-full is-size-7"><span class="has-text-weight-semibold">Completed tasks:</span> {{ todos.filter(t => t.completed === true).length }}</div>
            </li>
            <li class="columns">
                <div class="column is-full is-size-7"><span class="has-text-weight-semibold">Total tasks:</span> {{ todos.length }}</div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'TodoInfo',
    props: [ 'todos' ]
}
</script>