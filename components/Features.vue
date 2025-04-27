<script setup>
import { defineProps } from 'vue';
import sanitizeHtml from 'sanitize-html';

const props = defineProps({
  title: String,
  description: String,
  items: Array,
});

// Function to sanitize HTML
const sanitizeDescription = (description) => {
  return sanitizeHtml(description, {
    allowedTags: ['a', 'p', 'strong', 'em'], // Allow only specific tags
    allowedAttributes: {
      a: ['href', 'target', 'rel', 'class'], // Allow specific attributes for <a>
    },
  });
};
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
      v-for="item of items"
      class="p-8 border-2 border-dashed rounded-sm border-zinc-300 sm:p-12"
    >
      <div class="flex items-center gap-4">
        <img
          v-if="item.image"
          :src="`/${item.image}`"
          :alt="item.title"
          class="w-16 h-16 object-contain flex-shrink-0"
        />
        <h3
          v-if="item.title"
          class="text-2xl font-semibold text-zinc-800 flex-1"
        >
          {{ item.title }}
        </h3>
      </div>
      <p
        v-if="item.description"
        class="mt-4 text-zinc-500 leading-relaxed"
        v-html="sanitizeDescription(item.description)"
      ></p>
    </div>
  </div>
</template>