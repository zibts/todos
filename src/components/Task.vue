<template>
    <div @dblclick="this.$emit('toggle-reminder',task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>{{task.text}}</h3>
        <i @click="this.$emit('delete-task', task.id)" class="fas fa-times"></i>
        <p>{{task.day}}</p>
        <p>{{task.reminder}}</p>
    </div>
    
</template>
<script>
export default {
    name:'Task',
    props:{
        task:Object,
    },
    methods : {
    },
}
</script>