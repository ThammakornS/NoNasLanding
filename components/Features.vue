<script setup>
import { ref } from 'vue';
import DOMPurify from 'dompurify';

const props = defineProps({
  title: String,
  description: String,
  items: Array,
});

// Function to convert URLs to clickable links
function linkify(text) {
  const urlRegex = /(https?:\/\/[^\s)]+)/g;
  return text.replace(urlRegex, (url) => {
    return `<a href="${url}" target="_blank" rel="noopener noreferrer" class="text-blue-600 hover:underline">${url}</a>`;
  });
}

// Process descriptions for each item
const processedItems = ref(
  props.items.map((item) => ({
    ...item,
    description: DOMPurify.sanitize(linkify(item.description)),
  }))
);
</script>

<template>
  <h2
    class="text-3xl font-bold text-center text-zinc-800 sm:text-4xl"
    v-if="title"
  >
    {{ title }}
  </h2>
  <p
    class="max-w-3xl mx-auto mt-4 text-lg text-center text-zinc-600"
    v-if="description"
  >
    {{ description }}
  </p>
  <div class="grid gap-8 mt-10 mb-20 md:grid-cols-2">
    <div
      v-for="item of processedItems"
      class="p-8 border-2 border-dashed rounded-sm border-zinc-300 sm:p-12"
    >
      <!-- First row: Image (left) and Title (right) -->
      <div class="flex items-center gap-4">
        <!-- Image on the left -->
        <img
          v-if="item.image"
          :src="`/${item.image}`"
          :alt="item.title"
          class="w-16 h-16 object-contain flex-shrink-0"
        />
        <!-- Title on the right -->
        <h3
          v-if="item.title"
          class="text-2xl font-semibold text-zinc-800 flex-1"
        >
          {{ item.title }}
        </h3>
      </div>
      <!-- Second row: Description with clickable links -->
      <p
        v-if="item.description"
        class="mt-4 text-zinc-500 leading-relaxed"
        v-html="item.description"
      ></p>
    </div>
  </div>
</template>