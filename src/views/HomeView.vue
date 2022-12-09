<template>
  <main class="grid-container grid-container--home">
    <div>
      <h1 class="text-light fs-500 ff-sans-cond uppercase letter-spacing-1">So, you want to travel to <span class="block fs-900 ff-serif text-white">Space</span></h1>
      <p>Let’s face it; if you want to go to space, you might as well genuinely go to outer space and not hover kind of on the edge of it. Well sit back, and relax because we’ll give you a truly out of this world experience!</p>
    </div>
    <div>
      <a href="#" class="large-button uppercase ff-serif text-dark bg-white">Explore</a>
    </div>
  </main>
</template>

<script>

</script>

<style lang="scss" scoped>

@media (min-width: 60em) {
  .grid-container--home {
    padding-bottom: max(6rem, 20vh);
    align-items: end;
  }
.grid-container--home > *:first-child {
    grid-column: 2;
}
  .grid-container--home > *:last-child {
    grid-column: 3;
}
}

</style>
