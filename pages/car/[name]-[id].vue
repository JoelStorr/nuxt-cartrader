<script setup>
import { useFetchCar } from '#imports';

const route = useRoute();
const { toTitleCase } = useUtilities();

const {data: car} = await useFetchCar(route.params.id)
console.log(car)

useHead({
  title: toTitleCase(route.params.name),
});




definePageMeta({
  layout: "custom",
});
</script>
<template>
  <div>
    <CarDetailHero :car="car" />
    <CarDetailAttributes :features="car.features" />
    <CarDetailDescription :description="car.description" />
    <CarDetailContact />
  </div>
</template>