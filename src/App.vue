<template>
  <main class="columns is-gapless is-multiline" :class="{ 'modo-escuro': modoEscuroAtivo }"> <!-- Se o modo escuro está ativo a classe é adicionada, caso contrário, não.-->
    <div class="column is-one-quarter">
      <BarraLateral @aoTemaAlterado="trocarTema"/>
    </div>
    <div class="column is-three-quarter conteudo">
      <Formulario @aoSalvarTarefa="salvarTarefa"/>
      <div class="lista">
        <Tarefa v-for="(tarefa, index) in tarefas" :key="index" :tarefa="tarefa"/> <!--Para cada tarefa no array de tarefas, alguma coisa vai ser feita-->
        <!--Index é o índice que identifica o item do array-->
        <box v-if="listaEstaVazia">
        Você não está muito produtivo hoje :(
        </box>
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BarraLateral from './components/BarraLateral.vue';
import Formulario from './components/Formulario.vue';
import Box from './components/Box.vue'
import Tarefa from './components/Tarefa.vue';
import ITarefa from './interfaces/ITarefa';

export default defineComponent({
    name: 'App',
    components: {
      BarraLateral,
      Formulario,
      Tarefa,
      Box
    },
    data () {
      return {
        tarefas: [] as ITarefa[],
        modoEscuroAtivo: false 
      }
    },
    computed: {
      listaEstaVazia () : boolean {
        return this.tarefas.length === 0
      }
    },
    methods: {
      salvarTarefa (tarefa: ITarefa) {
        this.tarefas.push(tarefa)
      },
      trocarTema (modoEscuroAtivo: boolean) {
        this.modoEscuroAtivo = modoEscuroAtivo
    }
  }
});
</script>

<style>
.lista {
  padding: 1.25rem;
}
main {
  --bg-primario: #fff;
  --texto-primario: #000;
}

main.modo-escuro {
  --bg-primario: #2b2d42;
  --texto-primario: #ddd;
}
.conteudo {
  background-color: var(--bg-primario);
}
</style>
