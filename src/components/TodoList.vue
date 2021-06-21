<template>

  <div class="TodoList q-ml-xl q-mt-xl">

    <div class="tasklist q-mt-xl">
      <q-item-label class="text-h6" header>Task list</q-item-label>

        <TodoItem 
          v-for="t of Todolist" :key="t.id" 
          v-bind:task="t"
          v-on:RemoveTask="RemoveTask"
        />
    </div>

  </div>
</template>
<script>
import TodoItem from './TodoItem.vue'
export default {
  props:['Todolist'],
  data(){
    return{
      
    }
  },
  components:{
      TodoItem
    },
  methods:{
    RemoveTask(id){
      this.$emit('RemoveTask',id)
    }
  }
}
</script>
<style scoped>
li{
  list-style: none;
}
</style>