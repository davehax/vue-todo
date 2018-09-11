<template>
    <li>
        <span>{{ todo.text }}</span>
        <div>
            <!-- https://vuejs.org/v2/guide/forms.html#Checkbox -->
            <!-- v-model - todo.done : since this is an input
                    element, the v-model binding simply binds to
                    the boolean "todo.done" as the source of state -->
            <input v-model="todo.done" type="checkbox" />

            <!-- https://vuejs.org/v2/guide/syntax.html#Shorthands -->
            <!-- "@" is shorthand for "v-on:" -->
            <button type="button" @click="$emit('remove', todo.id)">&times;</button>
        </div>
    </li>
</template>

<script>
export default {
    name: "TodoItem",
    props: {
        todo: {
            type: Object,
            required: true
        }
    }
}
</script>
