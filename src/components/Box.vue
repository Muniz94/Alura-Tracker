<template>
  <div class="box has-text-weight-bold" :style="estilos">
    <slot></slot> <!--Renderiza o conteúdo do 'box'(nesse caso) para dentro dessa tag-->
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'Box',
  data() {
    return {
      estilos: {
        background: '#FAF0CA' // Se fosse background-color: teria que ser 'background-color' ou backgroundColor
      }
    }
  }
})
</script>

<!-- <style scoped> O que está acima equivale a isso
.box {
  background: #FAF0CA;
}
</style> -->