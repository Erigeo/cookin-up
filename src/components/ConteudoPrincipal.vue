<script lang="ts">
import SelecionarIngredientes from './SelecionarIngredientes.vue';
import SuaLista from './SuaLista.vue';
import Tag from './Tag.vue';

export default {
    data() {
        return {
            ingredientes: [] as String[]
        };
    },
    components: { SelecionarIngredientes, Tag, SuaLista },
    methods: {
      adicionarIngrediente(ingrediente: String){
        this.ingredientes.push(ingrediente)
      },
      removerIngrediente(ingrediente: String){
        this.ingredientes = this.ingredientes.filter(iLista => ingrediente !== iLista);
        //essa linha de codigo esta criando um novo array ingredientes, em que verifica se ja nao existem o tal ingrediente o comparando com os elementos existentes no array.
      }
    }
}
</script>


<template>
<main class="conteudo-principal">
  <SuaLista :ingredientes="ingredientes" />
    <SelecionarIngredientes
      @adicionar-ingrediente="adicionarIngrediente($event)"
       @remover-ingrediente="removerIngrediente($event)"
    />
</main>

</template>

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

.sua-lista-texto {
  color: var(--coral, #F0633C);
  display: block;
  text-align: center;
  margin-bottom: 1.5rem;
}

.ingredientes-sua-lista {
  display: flex;
  justify-content: center;
  gap: 1rem 1.5rem;
  flex-wrap: wrap;
}



.lista-vazia {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.25rem;

  color: var(--coral, #F0633C);
  text-align: center;
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