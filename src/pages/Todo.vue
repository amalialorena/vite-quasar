<template>
  <q-page class="q-pa-lg bg-grey-3 column">
    <q-list
        class="bg-white "
        separator
        bordered
    >
      <q-item
          v-for=" (task, i) in tasks"
          :class="{'done bg-blue-1': task.done}"
          :key='task.title + i'
          tag="label"
          v-ripple>
        <q-item-section avatar>
          <q-checkbox v-model="task.done"  color="primary" />
        </q-item-section>
        <q-item-section>
          <q-item-label>{{task.title}}</q-item-label>
        </q-item-section>
        <q-item-section
            v-if="task.done"
            side
        >
          <q-btn
              @click.stop="deleteTask(i)"
              flat
              dense
              color="primary"
              round
              icon="cancel" />
        </q-item-section>
      </q-item>

    </q-list>
  </q-page>
</template>

<script>

export default {
  data(){
    return {
      tasks: [
        {
          title: 'Iscrizione scuola',
          done: false
        },
        {
          title: 'Pagare doposcuola',
          done: false
        },
        {
          title: 'Cambiare medico',
          done: false
        },
        {
          title: ' Cambiare medico',
          done: false
        }
      ]
    }
  },
  methods: {
    deleteTask(i){
      this.$q.dialog({
        title: 'Confirm',
        message: 'Would you like to cancel this task?',
        cancel: true,
        persistent: true
      }).onOk(() => {
        this.tasks.splice(i,1)
      })
    }
  }
}
</script>

<style lang="css">
.done .q-item__label{
  text-decoration: line-through;
  color: #bbb;
}
</style>
