<template>
  <form @submit="onSubmit" action="add-form">
    <div class="form-control">
      <label>Task</label>
      <input type="text" name="text" placeholder="Add Task" v-model="text" />
    </div>
    <div class="form-control">
      <label>Day and time</label>
      <input type="text" name="day" placeholder="Add day and time" v-model="day" />
    </div>
    <div class="form-control form-control-check">
      <label>Set Reminder</label>
      <input type="checkbox" name="reminder" v-model="reminder" />
    </div>
    <input type="submit" value="Save Task" class="btn btn-block" />
  </form>

</template>


<script>
export default {
    name:'AddTask',
    data() { 
        return {
            text:'',
            day:'',
            reminder:''
        }
    },
    methods:{
        onSubmit(e) {
            e.preventDefault()

            if(!this.text) {
                alert('please ad task')
                return
            }

            const newTask = {
                id:Math.floor(Math.random() * 10000),
                text :this.text,
                day:this.day,
                reminder:this.reminder

            }

            this.$emit('add-task',newTask)
            
            this.text = '',
            this.day = '',
            this.reminder = false
            
        }
    }
};
</script>

<style scoped>

</style>