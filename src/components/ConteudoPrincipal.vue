<template>
  <main class="conteudo-principal">
    <SuaLista :ingredientes="ingredientes"/>
    <SelecionarIngredientes @selecionar-ingrediente="validaIngredientes"/>
    <BotaoPrincipal :texto="textoBotao"/>
  </main>
</template>

<script lang="ts">
import SelecionarIngredientes from './SelecionarIngredientes.vue';
import SuaLista from './SuaLista.vue';
import BotaoPrincipal from './BotaoPrincipal.vue';


export default {
  data() {
    return {
      ingredientes: [] as string[],
      textoBotao: "Buscar receitas!"
    }
  },
  components: {
    SelecionarIngredientes,
    SuaLista,
    BotaoPrincipal
  },
  methods: {
    validaIngredientes(ingrediente: string) {
      if (this.ingredientes.includes(ingrediente)) {
        this.ingredientes = this.ingredientes.filter(i => i !== ingrediente);
      } else {
        this.ingredientes.push(ingrediente);
      }
    }
  }
}
</script>

<style scoped>
.conteudo-principal {
  padding: 6.5rem 7.5rem;
  border-radius: 3.75rem 3.75rem 0rem 0rem;
  background: var(--creme, #FFFAF3);
  color: var(--cinza, #444);

  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5rem;
}
@media only screen and (max-width: 1300px) {
  .conteudo-principal {
    padding: 5rem 3.75rem;
    gap: 3.5rem;
  }
}

@media only screen and (max-width: 767px) {
  .conteudo-principal {
    padding: 4rem 1.5rem;
    gap: 4rem;
  }
}

</style>