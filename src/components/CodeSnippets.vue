<template>
  <section class="q-my-md">
    <q-card class="" dark>
      <q-card-section>
        <slot></slot>
      </q-card-section>
    </q-card>
  </section>
</template>

<script setup lang="ts">
defineOptions({
  name: 'codeSnippets',
});
</script>
