<script setup>
const route = useRoute();
useHead({
  title: `${
    route.params.make ? toTitleCase(route.params.make) : "Cars"
  } in ${toTitleCase(route.params.city)}`,
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
    <div class="mt-32 flex">
      <CarSideBar />
      <NuxtPage />
    </div>
  </div>
</template>
