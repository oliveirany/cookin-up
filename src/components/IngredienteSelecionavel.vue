<template>
  <button
    class="ingrediente"
    @click="selecionarIngrediente"
    :aria-pressed="selecionado"
  > 
    <Tag :texto="ingrediente" :ativa="selecionado" />
  </button>
</template>

<script lang="ts">
import Tag from './Tag.vue';

export default {
  components: {
    Tag
  },
  props: {
    ingrediente: {
      type: String,
      required: true
    }
  },
  data() { // estados
    return {
      selecionado: false
    }
  },
  methods: {
    selecionarIngrediente() {
      this.selecionado = !this.selecionado;
      this.$emit('selecionar-ingrediente', this.ingrediente);
    }
  },
  emits: [
    'selecionar-ingrediente'
  ]
}
</script>

<style scoped>
.ingrediente {
  cursor: pointer;
}
</style>