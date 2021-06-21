<template>
  <q-layout view="hHh lpR fFf">

    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar square>
            <img src="../assets/list.svg">
          </q-avatar>
          My Task
        </q-toolbar-title>
          <q-toggle v-model="toggleDark" color="black" checked-icon="dark_mode" unchecked-icon="light_mode" label="Dark mode" />
      </q-toolbar>
    </q-header>

    <q-page-container>

      <div class="title">
        <span class="text-h3 q-ml-xl">{{ Title }}</span>
        <q-separator class="q-mt-md" />
      </div>

      <AddTask class="q-ml-xl"
        @AddTask="AddTask"
      />

      <TodoList 
      :Todolist="Todolist"
      @RemoveTask="RemoveTask"

       />

      <router-view />
    </q-page-container>

    <q-footer elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          footer
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>

<script>
import TodoList from '../components/TodoList.vue'
import AddTask from '../components/AddTask.vue'
export default {
  name: 'PageIndex',
  data(){
    return {
      Title:'Todo list on quasar',
      Todolist:[
        {id:1, text:'Go to the gym', completed:false},
        {id:2, text:'Learn english', completed:false},
        {id:3, text:'Check todo lost', completed:false},
      ],
    }
  },
  components:{
      TodoList,AddTask
    },
  methods:{
    RemoveTask(id){
      this.Todolist = this.Todolist.filter(task => task.id !== id)
    },
    AddTask(newtask){
      this.Todolist.push(newtask)
    }
  },
  computed: {
    toggleDark: {
      get() {
        return this.$q.dark.isActive
      },
      set(val) {
        this.$q.dark.set(val)
      }
    }
  }
}
</script>
<style scoped>

</style>