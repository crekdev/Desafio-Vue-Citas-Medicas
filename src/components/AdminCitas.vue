<script>
import NewUserForm from './FormularioUsuario.vue'
import PatientCard from './Paciente.vue'

export default {
  name: 'AdminCitas',
  data() {
    return {
      pacientes: []
    }
  },
  components: { NewUserForm, PatientCard },
  methods: {
    agregarPaciente(nuevoPaciente) {
      this.pacientes.push(nuevoPaciente)
    },
    removeCard(idx) {
      this.pacientes.splice(idx, 1)
    }
  }
}
</script>

<template>
  <NewUserForm @submit-form="agregarPaciente" />
  <div v-show="pacientes.length == 0">
    <p class="text-center text-danger">No hay consultas registradas</p>
  </div>
  <div class="d-flex flex-wrap mt-5 gap-3">
    <PatientCard
      v-for="(paciente, idx) in pacientes"
      :key="idx"
      :paciente="paciente.paciente"
      :fecha="paciente.fecha"
      :hora="paciente.hora"
      :gravedad="paciente.gravedad"
      :motivo="paciente.motivo"
      @remove-card="removeCard(idx)"
    />
  </div>
</template>

<style scoped>

</style>
