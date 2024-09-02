<script>
export default {
  name: 'Paciente',
  props: ['paciente', 'fecha', 'hora', 'gravedad', 'motivo', 'idx'],
  methods: {
    removeCard() {
      this.$emit('remove-card')
    }
  },
  emits: 'remove-card'
}
</script>
<template>
  <div class="card mb-3 text-center" style="width: 18rem;"
    :class="gravedad === 'Baja' ? 'bg-success text-light' : gravedad === 'Media' ? 'bg-warning' : 'bg-danger text-light'">
    <div class="card-body">
      <b>Paciente:</b>
      <p>{{ paciente }}</p>
      <b>Fecha:</b>
      <p>{{ fecha }}</p>
      <b>Hora:</b>
      <p>{{ hora }}</p>
      <b>Motivo:</b>
      <p>{{ motivo }}</p>
      <button class="btn btn-dark" @click="removeCard">Eliminar</button>
    </div>
  </div>
</template>
<style scoped>

</style>
