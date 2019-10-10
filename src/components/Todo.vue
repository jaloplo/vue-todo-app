<template>
    <div id="todo-app" class="container">
        <div class="columns is-centered">
            <section class="column is-half">
                <TodoHeader />
                <TodoTaskForm @new-task="addTask" />
                <TodoList v-if="todos.length > 0" :todos="todos" @completeTask="completeTask" @deleteTask="deleteTask" @clearCompletedTasks="clearCompletedTasks" @markAllTasksAsCompleted="completeAllTasks"/>
                <TodoListEmpty v-if="todos.length < 1" />
                <TodoInfo v-if="todos.length > 0" :todos="todos" />        
            </section>
        </div>
    </div>
</template>

<script>
import TodoHeader from './todo/TodoHeader.vue'
import TodoTaskForm from './todo/TodoTaskForm.vue'
import TodoList from './todo/TodoList.vue'
import TodoListEmpty from './todo/TodoListEmpty.vue'
import TodoInfo from './todo/TodoInfo.vue'

export default {
    name: 'TodoApp',
    components: {
        TodoHeader,
        TodoTaskForm,
        TodoList,
        TodoListEmpty,
        TodoInfo
    },
    data() {
        return {
            todoNewTaskId: 4,
            todos: [
                { id: 1, title: 'Do not procrastinate', completed: false, importance: 'high' },
                { id: 2, title: 'Do homework', completed: false, importance: 'low' },
                { id: 3, title: 'Wash my teeth', completed: true, importance: 'medium' },
                { id: 4, title: 'Take a walk', completed: false, importance: 'medium' },
            ],
        };
    },
    methods: {
        addTask(taskTitle, importance) {
            this.todoNewTaskId += 1;
            this.todos.push(
                { id: this.todoNewTaskId, title: taskTitle, completed: false, importance: importance }
            );
        },

        clearCompletedTasks() {
            this.todos = this.todos.filter(t => t.completed === false);
        },

        completeAllTasks() {
            this.todos = this.todos.map(todo => {
                todo.completed = true;
                return todo;
            });
        },

        completeTask(todoItem) {
            this.todos.filter(t => t.id === todoItem.id).completed = !this.todos.filter(t => t.id === todoItem.id).completed;
        },

        deleteTask(todoItem) {
            this.todos = this.todos.filter(t => t.id !== todoItem.id);
        }
    }
}
</script>