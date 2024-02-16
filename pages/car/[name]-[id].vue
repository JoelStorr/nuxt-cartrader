<script setup>

    const route = useRoute()
    useHead({
        title:toTitleCase(route.params.name)
    })

     function toTitleCase(string) {
    return string.charAt(0).toUpperCase() + string.slice(1);
}

</script>


<template>
  <NavBar />
  <div>
    <div
      class="mx-auto mt-4 max-w-7xl space-y-4 px-4 xs:px-8 sm:px-10 lg:px-16 pb-16 w-3/5"
    >
      <CarDetailHero />

      <CarDetailAttributes />

      <CarDetailDescription />

      <CarDetailContact />
    </div>
  </div>
</template>
