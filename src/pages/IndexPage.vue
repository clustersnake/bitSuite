<template>
  <q-page class="q-px-md">
    <article>
      <header>
        <h3 v-if="entrada">{{ entrada }}</h3>
        <h3 v-else>0</h3>
      </header>
      <section>
        <q-input v-model.number="entrada" type="number" />
      </section>
      <section class="q-my-md">
        <header>Bits</header>
        <bits-array :numbers="entrada" />
      </section>
    </article>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import BitsArray from 'src/components/BitsArray.vue';

defineOptions({
  name: 'IndexPage',
});
const entrada = ref<number>(0);
</script>
