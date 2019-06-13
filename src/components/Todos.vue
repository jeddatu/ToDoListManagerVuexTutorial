<template>
    <div>
        <h3>Todos</h3>
        <div class="legend">
            <span>Double click to mark as complete</span>
            <span>
                <span class="incomplete-box"></span> = Incomplete
            </span>
            <span>
                <span class="complete-box"></span> = Complete
            </span>
        </div>
        <div class="todos">
            <div
                class="todo"
                @dblclick="onTodoDblClick(todo)"
                v-bind:key="todo.id"
                v-for="todo in allTodos"
                v-bind:class="{ 'completed-todo' : todo.completed }"
            >
                {{ todo.title }}
                <i
                    class="fas fa-trash-alt"
                    @click="deleteTodo(todo.id)"
                ></i>
                <!-- <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/> -->
            </div>    
        </div>    
    </div>
</template>

<script lang="ts">
import TodoItem from './TodoItem.vue';
import Vue from 'vue'
import { mapGetters, mapActions } from 'vuex';

export default Vue.extend({
    name: 'Todos',
    computed: mapGetters([
        'allTodos',    
    ]),
    created() {
        this.fetchTodos();
    },
    methods: {
        ...mapActions(
            [
                'deleteTodo',
                'fetchTodos',
                'updateTodo',
            ]
        ),
        onTodoDblClick(updTodo) {
            updTodo.completed = !updTodo.completed;
            this.updateTodo(updTodo);
        }
    },    
    props: ['todos']
})
</script>

<style scoped>
    .todos {
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-gap: 1rem;
    }

    .todo {
        border: 1px solid #ccc;
        background: #41b883;
        padding: 1rem;
        border-radius: 5px;
        text-align: center;
        position: relative;
        cursor: pointer;
    }

    .completed-todo {
        background: #35495e;
        color: #fff;
    }

    i {
        position: absolute;
        bottom: 10px;
        right: 10px;
        color: #fff;
        cursor: pointer; 
    }

    .legend {
        display: flex;
        justify-content: space-around;
        margin-bottom: 1rem;
    }

    .complete-box {
        display: inline-block;
        width: 10px;
        height: 10px;
        background: #35495e;
    }

    .incomplete-box {
        display: inline-block;
        width: 10px;
        height: 10px;
        background: #41b883;
    }

    @media (max-width: 500px) {
        .todos {
            grid-template-columns: 1fr;
        }
    }
</style>
