<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">

    <Cronometro :tempoEmsegundos="tempoEmsegundos" />
    <button class="button" @click="iniciar">
      <span class="icon">
        <i class="fas fa-play"></i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar">
      <span class="icon">
        <i class="fas fa-stop"></i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>

<script lang="ts">

  import { defineComponent } from 'vue'
  import Cronometro from './Cronometro.vue'

  export default defineComponent({
    name: 'Temporizador',
    components: {
      Cronometro
    },
    data () { // esse método define um estado inicial para o objeto
      return {
        tempoEmsegundos: 0,
        cronometro: 0
      }
    },
    methods: {
      iniciar () {
        // começar a contagem
        // 1 seg = 1000 ms
        this.cronometro = setInterval(() => {
          this.tempoEmsegundos += 1
        }, 1000)
      },
      finalizar () {
        clearInterval(this.cronometro);
      }
    }
  })

</script>