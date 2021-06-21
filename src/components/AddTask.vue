<template>
  <div class="adding q-pr-xl">

    <q-input v-model="text" label="Enter task" :error="isValid" bottom-slots>
      <template v-slot:error>
        Please enter your task
      </template>
    </q-input>

    <q-btn 
      class="q-mt-md" 
      color="primary" 
      icon="control_point" 
      label="Add Task"
      @click="AddNewTask"
    />
  </div>
</template>
<script>
export default {
  data() {
    return{
      text: '',
      isValid: false,
    }
  },
  methods:{
    AddNewTask(){
      if(this.text.trim()){
        const newtask = {
          id: Date.now(),
          text:this.text,
          completed: false
        };
        this.text = '';
        this.$emit('AddTask',newtask);
        this.isValid = false
      }else{
        this.isValid = !this.isValid
      }
    }
  }
}
</script>