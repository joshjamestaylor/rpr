<script setup lang="ts">
const navItems = [
  { label: 'Home', to: '/', icon: 'i-heroicons-home' },
  { label: 'Services', to: '/#services', icon: 'i-heroicons-wrench-screwdriver' },
  { label: 'Reviews', to: '/#reviews', icon: 'i-heroicons-star' },
  { label: 'Contact', to: '/#contact', icon: 'i-heroicons-envelope' },
]
</script>

<template>
  <UHeader :menu="{ shouldScaleBackground: true }">
    <template #title>
      <span class="font-bold text-lg">RPR Body Repairs</span>
    </template>

    <UNavigationMenu :items="navItems" class="hidden lg:flex" />

    <template #right>
      <UColorModeButton />
      <UButton
        to="/#contact"
        label="Get a Quote"
        color="primary"
        class="rounded-none hidden sm:inline-flex"
      />
    </template>

    <template #body>
      <UNavigationMenu :items="navItems" orientation="vertical" class="-mx-2.5" />
    </template>
  </UHeader>

  <UMain>
    <slot />
  </UMain>
</template>
