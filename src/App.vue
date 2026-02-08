<template>
  <TerminalLayout>
    <RouterView />
  </TerminalLayout>
</template>

<script setup>
import { RouterView } from 'vue-router'
import TerminalLayout from './layouts/TerminalLayout.vue'
</script>
