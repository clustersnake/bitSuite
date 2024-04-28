<template>
  <q-page class="q-px-md">
    <h3 class="">{{ entrada }}</h3>
    <article>
      <section class="q-my-md">
        <header>Bits</header>
        <bits-array :numbers="entrada" @onSetBit="onSetBit" />
        <!-- <q-btn
            v-for="(bit, idx) in bitButtons"
            :key="`bitBtn-${idx}`"
            :color="bit == '0' ? 'blue-grey-10' : 'dark'"
            :text-color="bit == '0' ? 'cyan-10' : 'cyan-4'"
            :icon="bit == '1' ? 'bi-1-square' : 'bi-0-square'"
            @click="onSetBit(idx)"
            padding="xs"
            :title="2**(Math.abs(idx-31))"
            push
          /> -->
      </section>
    </article>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import BitsArray from '../components/BitsArray.vue';

defineOptions({
  name: 'bitShiftPage',
});

const entrada = ref<number>(0);

const onSetBit = (val: number) => {
  debugger;
  entrada.value = val;
  // const pos = Math.abs(val - 31);
  // const bit = entrada.value & (1 << pos);
  // if (bit) {
  //   const mask = ~(1 << pos);
  //   entrada.value &= mask;
  // } else {
  //   entrada.value |= 2 ** pos;
  // }
};
//
// const bitButtons = computed(() => {
//   const num: number = entrada?.value || 0;
//
//   const val = num.toString(2);
//   if (val.length < 32) return '0'.repeat(32 - val.length) + val;
//
//   return val;
// });
</script>
