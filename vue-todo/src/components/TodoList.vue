<template>
    <div>
        <h1>Todo list in Vue.js</h1>
        <p>Enter text in then input and then press 'enter' to add a new todo item.</p>
        <!-- https://vuejs.org/v2/guide/components.html#Using-v-model-on-Components -->
        <!-- v-model -  -->
        <TodoInput 
            v-model="newTodoText"
            placeholder="New todo"
            @keydown.enter="addTodo"
        />
        <ul v-if="todos.length">
            <!-- v-for - for (todo in todos) { ... } -->
            <!-- v-bind:[prop] - bind data to a property of the custom Component -->
            <!-- @remove - bind an event handler to the event "remove" - denoted by the @ symbol -->
            <TodoItem
                v-for="todo in todos"
                v-bind:key="todo.id"
                v-bind:todo="todo"
                @remove="removeTodo"
            />
        </ul>
        <p v-else>No todo items. Add one!</p>
    </div>
</template>

<script>
import TodoInput from './TodoInput.vue';
import TodoItem from './TodoItem.vue';

let todoNextId = 1;

export default {
    components: {
        TodoInput, TodoItem
    },
    // data defines our state.
    // normally it would be a javascript object, but because
    // we're in a Custom Component it must become a FUNCTION.
    // This is to enable per-component state. This way, a higher
    // level component can instantiate many copies of <TodoList />
    // and each would have their own separate state.
    data () {
        return {
            // v-model binds to this
            newTodoText: '',
            // our todo items
            todos: [
                {
                    id: todoNextId++,
                    text: 'Learn more',
                    done: true
                },
                {
                    id: todoNextId++,
                    text: 'Keep learning',
                    done: true
                },
                {
                    id: todoNextId++,
                    text: 'In fact, never stop learning!',
                    done: false
                }
            ]
        }
    },
    // methods
    methods: {
        addTodo () {
            const trimmedText = this.newTodoText.trim();

            if (trimmedText) {
                // add a new todo item to our state
                this.todos.push({
                    id: todoNextId++,
                    text: this.newTodoText,
                    done: false
                });
                // reset the newTodoText
                // since v-model binds this property to
                // the Component it's passed to, changing it here
                // will affect the state of that Component
                this.newTodoText = '';
            }
        },
        removeTodo (idToRemove) {
            this.todos = this.todos.filter(todo => {
                return todo.id !== idToRemove
            });
        }
    }
}
</script>

