<template>
  <div class="is-flex os-align-items-center is-justify-content-space-between">
    <Hora :tempoEmSegundos="tempoEmSegundos" />
    <button class="button" @click="iniciar" :disabled="rodando">
      <span class="icon">
        <i class="fas fa-play"> </i>
      </span>
      <span>play</span>
    </button>
    <button class="button" @click="finalizar" :disabled="!rodando">
      <span class="icon">
        <i class="fas fa-stop"> </i>
      </span>
      <span>stop</span>
    </button>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";
import Hora from "./Hora.vue";
export default defineComponent({
  name: "TemporizadorVue",
  emits: ["aoTemporizadorFinalizado"],
  components: {
    Hora,
  },
  data() {
    return {
      tempoEmSegundos: 0,
      cronometro: 0,
      rodando: false,
    };
  },
  methods: {
    iniciar() {
      this.rodando = true;
      this.cronometro = setInterval(() => {
        this.tempoEmSegundos += 1;
      }, 1000);
    },
    finalizar() {
      this.rodando = false;
      clearInterval(this.cronometro);
      this.$emit("aoTemporizadorFinalizado", this.tempoEmSegundos);
      this.tempoEmSegundos = 0;
    },
  },
});
</script>
