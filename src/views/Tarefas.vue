<template>
  <div>
    <div>
      <v-col
         cols="12"
       >
       <v-text-field
          v-model="campoInput"
          label="Qual a sua tarefa?"
          outlined
          clearable
          @keyup.enter="handleAddTarefa"
         >
        </v-text-field>
      </v-col>
    <v-list
      flat
      subheader
    >

     <v-list-item-group
      multiple
      active-class=""
    >
      <div
       v-for="tarefa, index in $store.state.tarefas"
       :key="index"
      >
        <Tarefa
         :tarefa="tarefa" />
      </div>

      <Tarefa />
      <Tarefa />


       
      </v-list-item-group>
    </v-list>
 </div>

  </div>
</template>
 
<script>
import Tarefa from '../components/tarefas/Tarefa.vue'
  export default {
    name: 'Home',

    components: {
      Tarefa
    },
    data () {
      return {
        campoInput: null,
      }
    },
    methods: {
     handleAddTarefa () {
       //chamando a mutations
       this.$store.commit('adicionaTarefa', this.campoInput)
       this.campoInput = null
     }
    }
  }
</script>
