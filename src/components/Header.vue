<template>
    <header>
        <h1>{{title}}</h1>
        <Button @btn-click="$emit('toggle-add-task')" :btntext="showAddTask ? 'Close' : 'Add Task' "/>
    </header>
</template>

<script>
import Button from './Button'
export default {
    name:'Header',
    props:{
        title:String,
        showAddTask:Boolean,
    },
    components:{
        Button,
    }
}
</script>

<style scoped>
header {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
</style>