<template>
  <q-page class="q-px-md">
    <article>
      <header>
        <h3 v-if="entrada">{{ entrada }}</h3>
        <h3 v-else>0</h3>
      </header>
      <section class="q-my-md">
        <header>Bits</header>
        <bits-array :numbers="entrada" @onSetBit="onSetBit" />
      </section>
      <section class="q-my-md">
        <header>Código de ejemplo:</header>
        <code-snippets>
          <pre>
            // Encontrar el bit a modificar
            // *pos* indica la posición del bit seleccionado
            const bit = entrada &amp; (1 &lt;&lt; pos);
            if (bit) {
              // Si el bit está activo, se construye una máscara para 
              // desactivarlo y se aplica a la entrada usando el
              // operador AND
              const mask = ~(1 &lt;&lt; pos);
              entrada &amp;= mask;
            } else {
              // Si el bit está desactivado, se activa aplicando el 
              // operador OR
              entrada |= 2**pos;
            }
          </pre>
        </code-snippets>
      </section>
    </article>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import BitsArray from '../components/BitsArray.vue';
import CodeSnippets from '../components/CodeSnippets.vue';

defineOptions({
  name: 'orbitPage',
});

const entrada = ref<number>(0);

const onSetBit = (val: number) => {
  entrada.value = val;
};
</script>
