<template>
  <div class="mb-4 m-auto sm:mr-0 w-fit flex gap-2">
    <div class="p-2 rounded-md border flex items-center gap-1 has-[:focus]:border-cyan-500">
      <Search color="#7b7b7b" />
      <input type="text" class="outline-none" v-model="search" />
    </div>
    <button @click="collapseAll" class="border rounded-md p-2 active:border-cyan-500 active:scale-95 transition-transform">
      <Collapse color="#7b7b7b" />
    </button>
  </div>
  <ul v-if="filteredFaq.length > 0" class="flex flex-col gap-2">
    <CardItem v-for="item in filteredFaq" :answer="item.answer" :question="item.question" />
  </ul>
  <div v-else>
    <p>
      No results found for <span class="font-bold">{{ search }}</span>
    </p>
  </div>
</template>

<script setup lang="ts">
import { ref, watchEffect } from 'vue';

import faq from '../data/faq';
import Search from '../icons/Search.vue';
import CardItem from './CardItem.vue';
import Collapse from '../icons/Collapse.vue';

const filteredFaq = ref(faq);
const search = ref('');

watchEffect(() => {
  filteredFaq.value = faq.filter((item) => {
    return item.question.toLowerCase().includes(search.value.toLowerCase());
  });
});

function collapseAll() {
  document.querySelectorAll('details').forEach((item) => {
    item.removeAttribute('open');
  });
}
</script>

<style scoped></style>
