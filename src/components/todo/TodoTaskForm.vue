<template>
    <div class="todo-form">
        <div class="todo-form columns is-centered">
            <div class="column is-8">
                <div class="field">
                    <div class="control">
                        <input class="input" type="text" placeholder="type the title and choose the importance" v-model="title" />
                    </div>
                </div>
            </div>
        </div>
        <div class="todo-form columns is-centered">
            <div class="column is-4 has-text-centered">
                <div class="field is-grouped">
                    <div class="control">
                        <button class="button is-info is-outlined is-small" type="button" :disabled="'' === this.title" @click="addTask('low')">Low</button>
                    </div>
                    <div class="control">
                        <button class="button is-primary is-outlined is-small" type="button" :disabled="'' === this.title" @click="addTask('medium')">Medium</button>
                    </div>
                    <div class="control">
                        <button class="button is-danger is-outlined is-small" type="button" :disabled="'' === this.title" @click="addTask('high')">High</button>
                    </div>
                </div>
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
        addTask(importance) {
            this.$emit('new-task', this.title, importance);
            this.title = '';
        }
    }
}
</script>