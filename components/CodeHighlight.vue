<template>
  <pre><code ref="code" class="hljs" :class="language">{{ codeContent }}</code></pre>
</template>

<script setup>
import { ref, onMounted, watch } from 'vue';
import { useNuxtApp } from '#app';

const props = defineProps({
  codeContent: {
    type: String,
    required: true
  },
  language: {
    type: String,
    required: true
  }
});

const code = ref(null);
const { $hljs } = useNuxtApp();

onMounted(() => {
  if (code.value) {
    $hljs.highlightElement(code.value);
  }
});

watch(() => props.codeContent, () => {
  if (code.value) {
    $hljs.highlightElement(code.value);
  }
});
</script>

<style scoped>
pre {
  padding: 1em;
  background: #f5f5f5;
  border-radius: 5px;
}
</style>
