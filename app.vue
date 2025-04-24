<script setup>
useHead({
  htmlAttrs: { lang: "en-US" },
  title: "Indie Data Science",
  meta: [
    {
      name: "description",
      content:
        "We’re not your typical data science company. We build web tools that tackle the messy, overlooked, and just plain annoying parts of data work—like missing values, clunky prep, and the pain of trial-and-error modeling. Our tools aren’t trying to be everything. They’re sharp, focused, and built for folks who’d rather spend time thinking than cleaning.",
    },
  ],
  bodyAttrs: {
    class: 'font-display'
  }
});
</script>

<template>
  <NuxtLayout>
    <NuxtPage />
  </NuxtLayout>
</template>
