<template>
  <div>

  <q-list bordered class="q-mb-md">

   <q-item tag="label" v-ripple>
    <q-item-section side top>
      <q-checkbox v-model="value" />
    </q-item-section>

    <q-item-section>
      <q-item-label>{{task.text}}</q-item-label>
    </q-item-section>

    <q-item-section side >
      <q-btn round color="negative" size="md" icon="delete" v-on:click="$emit('RemoveTask',task.id)" />
    </q-item-section>
    </q-item>

  </q-list>

  </div>
</template>
<script>
export default {
props:{
  task:{
    type:Object,
    reqired:true,
  },
  index:{
    type:Number
  }
},
  data() {
   return{
     value:false,
   } 
  }
}
</script>