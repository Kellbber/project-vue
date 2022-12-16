<template>
  <div class="box has-text-weight-bold">
    <div class="columns">
      <div class="column is-7">{{tarefa.descricao || 'Tarefa sem descrição'}}</div>
      <div class="column">
        <Hora :tempoEmSegundos="tarefa.duracaoEmSegundos" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, PropType } from "vue";
import Hora from "./Hora.vue";
import ITarefa from "@/interface/ITarefa";
export default defineComponent({
  name: "TarefaVue",
  components: {
    Hora,
  },
  props: {
    tarefa: {
      type: Object as PropType<ITarefa>,
      required: true,
    },
  },
});
</script>

<style scoped>
.box {
  background-color: #faf0ca;
}
</style>
