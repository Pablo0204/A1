<template>
  <form class="contacto-form" @submit.prevent="validarFormulario">
    <div class="form-grid">
      <input class="form-input" v-model="nombre" placeholder="Nombre" />
      <input class="form-input" v-model="correo" placeholder="Correo" />
      <input class="form-input" v-model="telefono" placeholder="Teléfono" />
      <textarea class="form-textarea" v-model="mensaje" placeholder="Mensaje"></textarea>
    </div>

    <label class="checkbox-wrap">
      <input type="checkbox" v-model="newsletter" />
      <span>Suscribirse al boletín</span>
    </label>

    <button class="submit-button" type="submit">Enviar</button>
  </form>

  <div v-if="error" class="form-error">{{ error }}</div>

  <div v-if="enviado" class="form-summary">
    <h3>Datos enviados:</h3>
    <p><strong>Nombre:</strong> {{ nombre }}</p>
    <p><strong>Correo:</strong> {{ correo }}</p>
    <p><strong>Teléfono:</strong> {{ telefono }}</p>
    <p><strong>Mensaje:</strong> {{ mensaje }}</p>
    <p><strong>Boletín:</strong> {{ newsletter ? 'Sí' : 'No' }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nombre: '',
      correo: '',
      telefono: '',
      mensaje: '',
      newsletter: false,
      enviado: false,
      error: ''
    }
  },
  methods: {
    validarFormulario() {
      if (!this.nombre || !this.correo || !this.telefono || !this.mensaje) {
        this.error = 'Todos los campos son obligatorios';
        return;
      }
      this.enviado = true;
      this.error = '';
    }
  }
}
</script>
