<template>
    <button 
        :style="{background: color}" 
        class="btn"
        @click="onClick()">
        {{ text }}
    </button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: {
            type: String,
            default: 'Add Task Default'
        },
        color: String
    },
    methods: {
        onClick() {
            console.log("button clicked")
        }
    }
}
</script>
