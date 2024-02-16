<script setup>
const route = useRoute();
useHead({
  title: toTitleCase(route.params.name),
});

function toTitleCase(string) {
  return string.charAt(0).toUpperCase() + string.slice(1);
}

definePageMeta({
  layout: "custom",
});
</script>

<template>
  <div>
    <CarDetailHero />
    <CarDetailAttributes />
    <CarDetailDescription />
    <CarDetailContact />
  </div>
</template>
