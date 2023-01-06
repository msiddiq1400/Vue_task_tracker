<template>
    <div :class="[task.reminder ? 'reminder': '', 'task']">
        <h3>
            {{ task.text }}
            <i class="fas fa-times"></i>
        </h3>
        <p>{{ task.day }}</p>

    </div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object
    }
}
</script>

<style scoped>
div {
    background: #f4f4f4;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
}
h3 {
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.reminder {
    border-left: 5px solid green;
}

.fas {
    color: red;
}
</style>
