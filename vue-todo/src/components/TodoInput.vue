<template>
    <!-- https://vuejs.org/v2/guide/components.html#Using-v-model-on-Components -->
    <input
        type="text"
        class="input"
        v-bind:value="value"
        v-on="listeners"
    />
</template>

<script>
export default {
    // Properties
    props: {
        value: {
            type: String,
            default: 'New item'
        }
    },
    // This is short for "Computed Properties"
    computed: {
        
        listeners () {
            return {
                // Pass through Component Listeners
                ...this.$listeners,

                // Attach our own "input" listener that captures the 'input'
                // event and transforms the response value from 'event'
                // to 'event.target.value' so that v-model works correctly
                // with our Custom Component

                // https://vuejs.org/v2/guide/components.html#Using-v-model-on-Components
                // from https://codesandbox.io/s/o29j95wx9
                // In "TodoList.vue", note the line "v-model="newTodoText"
                // without the below, "newTodoText" value would be set to "event" rather
                // than what you would expect, which is event.target.value
                input: event => this.$emit('input', event.target.value)
            }
        }
    }
}
</script>

<style>
.input {
    width: 100%;
    padding: 3px 6px;
}
</style>


