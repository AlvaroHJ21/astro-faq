<template>
  <li>
    <details>
      <summary
        class="select-none list-none border p-4 rounded-md font-semibold hover:border-cyan-500"
      >
        {{ props.question }}
      </summary>
      <div class="p-4" v-html="props.answer" />
    </details>
  </li>
</template>

<script setup lang="ts">
interface Props {
  question: string;
  answer: string;
}

const props = defineProps<Props>();
</script>
