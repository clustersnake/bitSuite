<template>
  <q-page class="q-px-md">
    <h3 class="">{{ entrada }}</h3>
    <article>
      <section>
        <q-input v-model.number="entrada" type="number" />
      </section>
      <section class="q-my-md">
        <header>Bits</header>
        <q-btn
          v-for="(bit, idx) in bitButtons"
          :key="`bitBtn-${idx}`"
          :label="bit"
          :color="bit == '1' ? 'primary' : ''"
          :text-color="bit == '0' ? 'black' : ''"
        />
      </section>
      <section>
        <q-btn icon="keyboard_double_arrow_left" @click="moveLeft" />
        <q-btn icon="keyboard_double_arrow_right" @click="moveRight" />
      </section>
    </article>
  </q-page>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue';

defineOptions({
  name: 'bitShiftPage',
});

const entrada = ref<number>(1);

const moveLeft = () => {
  if (entrada.value < 2 ** 30) entrada.value <<= 1;
};
const moveRight = () => {
  if (entrada.value >= 2 ** 0) entrada.value >>= 1;
};

const bitButtons = computed(() => {
  const num: number = entrada?.value || 0;

  const val = num.toString(2);
  if (val.length < 32) return '0'.repeat(32 - val.length) + val;

  return val;
});
</script>
