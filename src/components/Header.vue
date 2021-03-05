<template>
    <header>
        <h1>{{title}}</h1>
        <Button v-show="homePage" @btn-click="$emit('toggle-add-task')" :btntext="showAddTask ? 'Close' : 'Add Task' "/>
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
    },
    computed : {
        homePage () { 
            if(this.$route.path ==='/') {
                return true
            } else {
                return false
            }
        }
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