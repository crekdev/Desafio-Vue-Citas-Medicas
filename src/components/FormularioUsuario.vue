<script>
export default {
  name: 'FormularioUsuario',
  data() {
    return {
      paciente: '',
      hora: '',
      fecha: '',
      gravedad: '',
      optionGravedad: ['Baja', 'Media', 'Alta'],
      motivo: ''
    }
  },
  methods: {
    addPaciente() {
      this.$emit('submit-form', {
        paciente: this.paciente,
        hora: this.hora,
        fecha: this.fecha,
        gravedad: this.gravedad,
        motivo: this.motivo
      })

      // Limpiamos formulario
      this.paciente = ''
      this.fecha = ''
      this.hora = ''
      this.gravedad = ''
      this.motivo = ''
    },
    isFormValid() {
      console.log('Validando form')
      return this.paciente && this.fecha && this.hora && this.gravedad && this.motivo
    }
  },
  emits: ['submit-form']
}
</script>
<template>
  <h1 class="text-center mb-3">Citas Médicas</h1>
  <form class="shadow p-5 border border-dark-subtle rounded-3" @submit.prevent="addPaciente">
    <div class="row g-3">
      <div class="col">
        <label for="paciente" :class="paciente === '' ? 'text-danger' : 'text-black'">Paciente</label>
        <input type="text" class="form-control" placeholder="Nombre de paciente" aria-label="Paciente" id="paciente"
          v-model="paciente">
      </div>
      <div class="col">
        <label for="fecha" :class="fecha === '' ? 'text-danger' : 'text-black'">Fecha</label>
        <input type="date" class="form-control" placeholder="Fecha" aria-label="fecha" id="fecha"
          v-model="fecha">
      </div>
      <div class="col">
        <label for="hora" :class="hora === '' ? 'text-danger' : 'text-black'">Hora</label>
        <input type="time" class="form-control" placeholder="Hora" aria-label="hora" id="hora" v-model="hora">
      </div>
      <div class="col">
        <label for="gravedad" :class="gravedad === '' ? 'text-danger' : 'text-black'">Gravedad</label>
        <select id="gravedad" class="form-select" v-model="gravedad">
          <option v-for="(option, idx) in optionGravedad" :key="idx">{{ option }}</option>
        </select>
      </div>
      <div class="col">
        <label for="motivo" :class="motivo === '' ? 'text-danger' : 'text-black'">Motivo</label>
        <input type="text" class="form-control" placeholder="Motivo de consulta" aria-label="Motivo" id="motivo"
          v-model="motivo">
      </div>
    </div>
    <div class="text-center">
      <button class="btn btn-dark mt-3" type="submit" :disabled="!isFormValid()">Agregar</button>
    </div>
  </form>
</template>
<style>
</style>
