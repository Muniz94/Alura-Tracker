<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometro :tempoEmsegundos="tempoEmsegundos"/>
    <Botao @clicado="iniciar" icone="fas fa-play" texto="play" :desabilitado="cronometroRodando" />
    <Botao @clicado="finalizar" icone="fas fa-stop" texto="stop" :desabilitado="!cronometroRodando" /> <!-- o dois pontos linka o estado do objeto com o atributo disabled -->
  </div>
</template>

<script lang="ts">

  import { defineComponent } from 'vue'
  import Cronometro from './Cronometro.vue'
  import Botao from './Botao.vue'

  export default defineComponent({
    name: 'Temporizador',
    emits: ['aoTemporizadorFinalizado'],
    components: {
      Cronometro,
      Botao
    },
    data () { // esse método define um estado inicial para o objeto
      return {
        tempoEmsegundos: 0,
        cronometro: 0,
        cronometroRodando: false,
      }
    },
    methods: {
      iniciar () {
        // começar a contagem
        // 1 seg = 1000 ms
        this.cronometroRodando = true
        this.cronometro = setInterval(() => {
          this.tempoEmsegundos += 1
        }, 1000)
      },
      finalizar () {
        this.cronometroRodando = false
        clearInterval(this.cronometro);
        this.$emit('aoTemporizadorFinalizado', this.tempoEmsegundos)
        this.tempoEmsegundos = 0
      }
    }
  })

</script>