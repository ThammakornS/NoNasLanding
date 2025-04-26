<script setup>
import pageData from '@/data/index.json'
const page = ref(pageData)

definePageMeta({
  layout: "default",
});
</script>

<template>
  <Container>
    <!-- Hero section -->
    <section>
    <Hero
      :title="page.hero.title"
      :description="page.hero.description"
      :image="page.hero.image"
      :imageAlt="page.hero.imageAlt"
      :buttons="page.hero.buttons"
    ></Hero>
    </section>

    <!-- Logos section with id -->
    <section>
    <Logos :title="page.logos.title" :icons="page.logos.icons"></Logos>
    </section>

    <!-- Features section with id -->
    <section id="features">
    <Features
      :title="page.features.title"
      :description="page.features.description"
      :items="page.features.items"
    ></Features>
    </section>

    <!-- Testimonials section with id -->
    <section>
    <Testimonials
      :title="page.testimonials.title"
      :description="page.testimonials.description"
      :items="page.testimonials.items"
    ></Testimonials>
    </section>

    <!-- Cta section with id -->
    <!-- <section>
    <Cta
      :title="page.cta.title"
      :description="page.cta.description"
      :buttons="page.cta.buttons"
    ></Cta>
    </section> -->

  </Container>
</template>
