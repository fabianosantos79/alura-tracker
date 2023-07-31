<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }">
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema" />
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa='salvarTarefa' />
      <div class="lista">
        <TarefaItem v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa" />
        <BoxItem v-if="listaEstaVazia">
          Você não está produtivo hoje :(
        </BoxItem>
      </div>
    </div>
  </main>
</template>



<script lang="ts">
import { defineComponent } from 'vue'
import BarraLateral from './components/BarraLateral.vue'
import Formulario from './components/Formulario.vue'
import TarefaItem from './components/TarefaItem.vue';
import ITarefa from './interfaces/ITarefa'
import BoxItem from './components/BoxItem.vue';

export default defineComponent({
  name: 'App',
  components: {
    BarraLateral,
    Formulario,
    TarefaItem,
    BoxItem
  },
  data() {
    return {
      tarefas: [] as ITarefa[],
      modoEscuroAtivo: false
    }
  },
  computed: {
    listaEstaVazia(): boolean {
      return this.tarefas.length === 0
    }
  },
  methods: {
    salvarTarefa(tarefa: ITarefa) {
      this.tarefas.push(tarefa)
    },
    trocarTema(modoEscuroAtivo: boolean) {
      this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>



<style>
.lista {
  padding: 1.5rem;
}

main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #fff;
}

.conteudo {
  background-color: var(--bg-primario);
}
</style>
