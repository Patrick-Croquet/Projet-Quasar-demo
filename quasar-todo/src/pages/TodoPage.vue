<template>
  <q-page class="bg-grey-3 column">
    <div class="row q-pa-sm bg-primary">
      <q-input 
        v-model="newTask"
        @keyup.enter="addTask" 
        class="col" 
        square 
        filled 
        bg-color="white" 
        placeholder="Add task" 
        dense>
        <template v-slot:append>
          <q-btn 
            @click="addTask"
            round 
            dense 
            flat 
            icon="add" />
        </template>
      </q-input>
    </div>
    <q-list class="bg-white" separator bordered>
      <q-item v-for="(task,index) in tasks" :key="task.title" @click="task.done=!task.done"
        :class="{'done bg-blue-1': task.done}" clickable v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="task.done" class="no-pointer-events" color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{ task.title }}</q-item-label>
        </q-item-section>
        <q-item-section v-if="task.done" side>
          <q-btn @click.stop="deleteTask(index)" flat round dense color="primary" icon="delete" />
        </q-item-section>
      </q-item>

      <!-- <q-item tag="label" v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="color" val="orange" color="orange" />
        </q-item-section>
        <q-item-section>
          <q-item-label>Orange</q-item-label>
          <q-item-label caption>With description</q-item-label>
        </q-item-section>
      </q-item>

      <q-item tag="label" v-ripple>
        <q-item-section avatar top>
          <q-checkbox v-model="color" val="cyan" color="cyan" />
        </q-item-section>
        <q-item-section>
          <q-item-label>Cyan</q-item-label>
          <q-item-label caption>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod
            tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam,
            quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo
            consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
            cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat
            non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
          </q-item-label>
        </q-item-section>
      </q-item> -->
    </q-list>
    <div
      v-if="!tasks.length"
      class="no-tasks absolute-center">
      <q-icon
        name="check"
        size="100px"
        color="primary"/>
      <div class="text-h5 text-primary text-center">
        No tasks
      </div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TodoPage',

  data() {
    return {
      newTask: '',
      tasks: [
        // {
        //   title: 'Get bananas',
        //   done: false
        // },
        // {
        //   title: 'Eat bananas',
        //   done: false
        // },
        // {
        //   title: 'Poo bananas',
        //   done: false
        // }
      ]
    }
  },
  methods: {
    deleteTask(index){
      this.$q.dialog({
        title: 'Confirm',
        message: 'Really delete?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        this.tasks.splice(index,1)
        this.$q.notify('Task deleted')
      })  
    },
    addTask() {
      // console.log('addTask')
      this.tasks.push({
        title: this.newTask,
        done:false
      }),
      this.newTask =''
    }
  }
})
</script>

<style lang="scss">
  .done {
    .q-item__label {
      text-decoration: line-through;
      color: #bbb;
    }
  }
  .no-tasks {
    opacity: 0.5;
  }
</style>