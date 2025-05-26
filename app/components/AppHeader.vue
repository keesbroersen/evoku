<script setup lang="ts">
const route = useRoute();

const items = computed(() => [
  {
    label: "Werk",
    to: "/werk",
    active: route.path.startsWith("/werk"),
  },
  {
    label: "Over",
    to: "/over",
    active: route.path.startsWith("/over"),
  },
  {
    label: "Contact",
    to: "/contact",
    active: route.path.startsWith("/contact"),
  },
]);
</script>

<template>
  <UHeader>
    <template #left>
      <NuxtLink to="/">
        <Logo class="w-auto h-8 shrink-0" />
      </NuxtLink>
    </template>

    <UNavigationMenu :items="items" variant="link" />

    <template #right>
      <UColorModeButton />

      <!-- <UButton
        icon="i-lucide-log-in"
        color="neutral"
        variant="ghost"
        to="/login"
        class="lg:hidden"
      />

      <UButton
        label="Sign in"
        color="neutral"
        variant="outline"
        to="/login"
        class="hidden lg:inline-flex"
      />

      <UButton
        label="Sign up"
        color="neutral"
        trailing-icon="i-lucide-arrow-right"
        class="hidden lg:inline-flex"
        to="/signup"
      /> -->
    </template>

    <template #body>
      <UNavigationMenu :items="items" orientation="vertical" class="-mx-2.5" />

      <USeparator class="my-6" />

      <!-- <UButton
        label="Sign in"
        color="neutral"
        variant="subtle"
        to="/login"
        block
        class="mb-3"
      />
      <UButton label="Sign up" color="neutral" to="/signup" block /> -->
    </template>
  </UHeader>
</template>
