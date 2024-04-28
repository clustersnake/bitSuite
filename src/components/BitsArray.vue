<template>
  <section class="q-my-md">
    <q-btn
      v-for="(bit, idx) in bitButtons"
      :key="`bitBtn-${idx}`"
      :color="bit == '0' ? 'blue-grey-10' : 'dark'"
      :text-color="bit == '0' ? 'cyan-10' : 'cyan-4'"
      :icon="bit == '1' ? 'bi-1-square' : 'bi-0-square'"
      @click="onSetBit(idx)"
      padding="xs"
      :title="2 ** Math.abs(idx - 31)"
      push
    />
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps({
  numbers: {
    type: Number,
    required: true,
  },
});
const emit = defineEmits(['onSetBit']);

defineOptions({
  name: 'bitShiftPage',
});

const onSetBit = (val: number) => {
  console.log(val);
  debugger;
  if (props.numbers >= 0) {
    let newValue: number = props.numbers || 0;
    const pos = Math.abs(val - 31);
    const bit = newValue & (1 << pos);
    if (bit) {
      const mask = ~(1 << pos);
      newValue &= mask;
    } else {
      newValue |= 2 ** pos;
    }
    emit('onSetBit', newValue);
  }
};

const bitButtons = computed(() => {
  debugger;
  const num: number = props.numbers || 0;

  const val = num.toString(2);
  if (val.length < 32) return '0'.repeat(32 - val.length) + val;

  return val;
});
</script>
