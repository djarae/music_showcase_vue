<template>
  <button 
    class="
      px-6 py-2 
      border-2 border-[var(--color-primary)] 
      text-[var(--color-primary)] 
      bg-transparent 
      font-mono text-lg font-bold
      uppercase tracking-wider
      hover:bg-[var(--color-primary)] hover:text-black
      transition-all duration-300
      focus:outline-none focus:ring-2 focus:ring-[var(--color-primary)] focus:ring-opacity-50
      terminal-box-shadow
    "
    @click="$emit('click')"
  >
    <slot></slot>
  </button>
</template>

<script setup>
defineEmits(['click'])
</script>
