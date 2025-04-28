<script setup>
import pageData from '@/data/index.json'
const page = ref(pageData)

definePageMeta({
  layout: "default",
});

// Enhance SEO with page-specific metadata
useHead({
  title: "Indie Data Science - Tools for Smarter Data Work",
  meta: [
    {
      name: "description",
      content: page.hero.description, // Use hero description from index.json
    },
    {
      name: "keywords",
      content: "data science tools, missing data, SMOTE, dimensionality reduction, time series, indie data science",
    },
    // Open Graph for social media
    {
      property: "og:title",
      content: "Indie Data Science - Tools for Smarter Data Work",
    },
    {
      property: "og:description",
      content: page.hero.description,
    },
    {
      property: "og:image",
      content: `/${page.hero.image}`, // Use hero image from index.json
    },
    {
      property: "og:url",
      content: "https://yourdomain.com", // Replace with your domain
    },
    {
      property: "og:type",
      content: "website",
    },
    // Twitter Card
    {
      name: "twitter:card",
      content: "summary_large_image",
    },
    {
      name: "twitter:title",
      content: "Indie Data Science - Tools for Smarter Data Work",
    },
    {
      name: "twitter:description",
      content: page.hero.description,
    },
    {
      name: "twitter:image",
      content: `/${page.hero.image}`,
    },
  ],
});
</script>