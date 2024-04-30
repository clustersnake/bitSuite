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
      <section>
        <q-btn
          icon="keyboard_double_arrow_left"
          @click="moveLeft"
          color="dark"
          text-color="cyan-4"
          push
        />
        <q-btn
          icon="keyboard_double_arrow_right"
          @click="moveRight"
          color="dark"
          text-color="cyan-4"
          push
        />
      </section>
      <section class="q-my-md">
        <header>Código de ejemplo:</header>
        <code-snippets>
          <pre>
            // Mover un bit hacia la izquierda
            const moveLeft = () =&gt; {
              // Se valida si el bit está por abajo del 
              // valor máximo de 31 bits 
              if (entrada.value &lt; 2**30) {
                // desplazar el bit una posición hacia la izquierda
                entrada.value &lt;&lt;= 1;
              }
            };

            // Mover un bit hacia la derecha
            const moveRight = () =&gt; {
              // Se valida si el bit está por encima del 
              // valor mínimo de 0 bits 
              if (entrada.value &gt;= 2**0) { 
                // desplazar el bit una posición hacia la derecha
                entrada.value &gt;&gt;= 1;
              }
            };
          </pre>
        </code-snippets>
      </section>
    </article>
  </q-page>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import BitsArray from 'src/components/BitsArray.vue';
import CodeSnippets from 'src/components/CodeSnippets.vue';

defineOptions({
  name: 'bitShiftPage',
});

const entrada = ref<number>(1);

const moveLeft = () => {
  if (entrada.value < 2**30) entrada.value <<= 1;
};
const moveRight = () => {
  if (entrada.value >= 2**0) entrada.value >>= 1;
};
</script>
