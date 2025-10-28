<script setup>
import { computed } from 'vue'

const props = defineProps({
  type: { type: String, default: 'info' },
  width: { type: String, default: '' }
})

// Map type -> icon, title, color scheme
const typeMap = {
  info:     { title: 'Note',      icon: 'ℹ️',  bg: '#e0f2fe', border: '#0ea5e9', text: '#0369a1' },
  tip:      { title: 'Tip',       icon: '💡',  bg: '#d1fae5', border: '#10b981', text: '#065f46' },
  warning:  { title: 'Warning',   icon: '⚠️',  bg: '#fef3c7', border: '#f59e0b', text: '#78350f' },
  caution:  { title: 'Caution',   icon: '❗',  bg: '#fee2e2', border: '#ef4444', text: '#991b1b' },
  important:{ title: 'Important', icon: '🛑',  bg: '#f3e8ff', border: '#a855f7', text: '#581c87' }
}

const currentType = computed(() => typeMap[props.type] || typeMap.info)
</script>

<template>
  <div
    class="admonition-box"
    :style="{
      width: props.width,
      maxWidth: '90%',
      backgroundColor: currentType.bg,
      borderColor: currentType.border,
      color: currentType.text
    }"
  >
    <div class="admonition-title">
      <span class="icon">{{ currentType.icon }}</span>
      <span class="title">{{ currentType.title }}</span>
    </div>
    <div class="admonition-content">
      <slot />
    </div>
  </div>
</template>


<style scoped>
.admonition-box {
  display: inline-block;
  width: auto;
  max-width: 90%;
  word-wrap: break-word;
  overflow-wrap: anywhere;
  padding: 8px 16px;
  margin: 6px 0;
  border-radius: 6px;
  border: 1px solid;
  border-left-width: 6px;
  font-size: 0.85rem;
  font-family: var(--neversink-main-font, sans-serif);
}

.admonition-title {
  display: flex;
  align-items: center;
  gap: 6px;
  font-weight: 700;
  margin-bottom: 4px;
}

.icon {
  font-size: 1rem;
}

.admonition-content {
  line-height: 1.35;
  margin: 0;
}
</style>
