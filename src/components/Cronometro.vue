<template>
  <section>
    <strong class="display">
      {{ tempoDecorrido }}
    </strong>
  </section>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Cronômetro',
  props: { // Propriedades que vamos receber do componente pai(Formulário) para o componente filho(Cronômetro) 
    tempoEmSegundos: {
      type: Number,
      default: 0
    }
  },
    computed: {
    tempoDecorrido() : string {
      return new Date(this.tempoEmSegundos * 1000).toISOString().substr(11, 8) // new Date().toISOString() = '2023-10-08T23:48:23.034Z'
      // substring(11,8) para pegar só o que interessa HH : MM : SS
    }
  },
})
</script>

<style scoped>
.display {
  color: var(--texto-primario);
}
</style>