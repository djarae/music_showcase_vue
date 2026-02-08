<template>
  <div class="flex flex-col gap-1">
    <label v-if="label" class="text-[var(--color-primary)] font-mono text-sm uppercase">{{ label }}</label>
    <input 
      :type="type" 
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      :placeholder="placeholder"
      class="
        w-full px-4 py-2
        bg-black
        border-b-2 border-[var(--color-primary)] 
        text-[var(--color-primary)] font-mono
        placeholder-opacity-50 placeholder-[var(--color-primary)]
        focus:outline-none focus:bg-[var(--color-surface)]
        transition-colors duration-300
      "
    />
  </div>
</template>

<script setup>
defineProps({
  modelValue: String,
  label: String,
  type: {
    type: String,
    default: 'text'
  },
  placeholder: String
})

defineEmits(['update:modelValue'])
</script>
