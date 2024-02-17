<template>
  <li>
    <details>
      <summary
        class="select-none list-none border p-4 rounded-md font-semibold hover:border-cyan-500"
      >
        {{ faq.question }}
      </summary>
      <div class="p-4 answer" v-html="parse(faq.answer)" />
    </details>
  </li>
</template>

<script setup lang="ts">
import type { Faq } from '../interfaces/Faq';
import { parse } from 'marked';

interface Props {
  faq: Faq;
}

defineProps<Props>();
</script>

<style>
/* h1,
p,
ul {
  margin-bottom: 0.5rem;
} */

.answer {
  h1,
  h2,
  h3,
  p,
  ul {
    margin-bottom: 0.5rem;
  }

  h1,
  h2,
  h3 {
    font-weight: 600;
  }

  ul {
    list-style-type: disc;
    padding-left: 2rem;
  }
}
</style>
