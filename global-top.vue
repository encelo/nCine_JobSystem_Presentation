<template>
  <SlidevSpotlight/>

  <footer
    v-if="$nav.currentLayout !== 'cover'"
    class="absolute top-0 right-0 p-2"
  >
    {{ $nav.currentPage }} / {{ $nav.total }}
  </footer>
  <footer
    v-if="$nav.currentLayout !== 'cover'"
    class="absolute bottom-0 right-0 p-2"
  >
    <span class="text-xs"><carbon-group-presentation /> The nCine Job System</span>
  </footer>
</template>
