<template>

    <button @click="onClick()" :style="{ background: color }" 
    class="btn">Add Task</button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        Text: String,
        color: String
    },
    methods: {
        onClick() {
            this.$emit('btn-click')
        }
    }
}
</script>