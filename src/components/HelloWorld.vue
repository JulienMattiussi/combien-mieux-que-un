<script setup lang="ts">
import { ref } from "vue";

defineProps<{ msg: string }>();

const combien = ref(1);
const resultat = ref(1);

const initCombien = () => {
  combien.value = 1;
  resultat.value = 1;
};

const updateCombien = () => {
  combien.value++;
  if (combien.value > 6) {
    resultat.value = resultat.value - combien.value;
    return;
  }

  resultat.value = resultat.value + combien.value;
};
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <button type="button" @click="updateCombien">
      {{ combien }} c'est
      {{
        resultat < 0 ? `${-resultat} fois moins bien` : `${resultat} fois mieux`
      }}
      que 1
    </button>
  </div>

  <div class="card">
    <button type="button" @click="initCombien">Reinit</button>
  </div>

  <p>Based on an idea from Antoine</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
