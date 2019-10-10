<template>
    <div id="todo-app" class="container">
        <div class="columns is-centered">
            <section class="column is-half">
                <TodoHeader />
                <TodoTaskForm @new-task="addTask" />
                <TodoList :todos="todos" @completeAllTasks="completeAllTasks" @completeTask="completeTask"/>
                <TodoInfo :todos="todos" />                
            </section>
        </div>
    </div>
</template>

<script>
import TodoHeader from './todo/TodoHeader.vue'
import TodoTaskForm from './todo/TodoTaskForm.vue'
import TodoList from './todo/TodoList.vue'
import TodoInfo from './todo/TodoInfo.vue'

export default {
    name: 'TodoApp',
    components: {
        TodoHeader,
        TodoTaskForm,
        TodoList,
        TodoInfo
    },
    data() {
        return {
            todos: [
                { id: 1, title: 'Do not procrastinate', completed: false },
                { id: 2, title: 'Do homework', completed: false },
                { id: 3, title: 'Wash my teeth', completed: true },
                { id: 4, title: 'Take a walk', completed: false },
            ],
        };
    },
    methods: {
        addTask(taskTitle) {
            this.todos.push(
                { id: this.todos.length + 1, title: taskTitle, completed: false }
            );
        },

        completeAllTasks() {
            this.todos = this.todos.map(todo => {
                todo.completed = true;
                return todo;
            });
        },

        completeTask(todoItem) {
            this.todos[todoItem.id-1].completed = !this.todos[todoItem.id-1].completed;
        }
    }
}
</script>