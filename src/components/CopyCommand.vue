<script setup lang="ts">
import { ref } from "vue";

const props = defineProps<{ command: string }>();

const copied = ref(false);
let timer: ReturnType<typeof setTimeout> | undefined;

async function copy() {
  try {
    await navigator.clipboard.writeText(props.command);
    copied.value = true;
    if (timer) clearTimeout(timer);
    timer = setTimeout(() => {
      copied.value = false;
    }, 1500);
  } catch {
    copied.value = false;
  }
}
</script>

<template>
  <div class="flex items-center justify-between gap-4 rounded-lg border border-line bg-night px-4 py-2.5 font-mono text-sm">
    <code class="overflow-x-auto whitespace-pre text-ink"><span class="select-none text-leaf">$ </span>{{ command }}</code>
    <button
      type="button"
      class="shrink-0 rounded-md border border-line px-2.5 py-1 text-xs text-dim transition hover:border-dim hover:text-ink"
      @click="copy"
    >
      {{ copied ? "Copied" : "Copy" }}
    </button>
  </div>
</template>
