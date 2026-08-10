<template>
  <div class="section-block">
    <h3 class="section-title">{{ field.label }}</h3>
    <p v-if="field.description" class="section-description">{{ field.description }}</p>
  </div>
</template>

<script setup lang="ts">
import type { FormField } from "@/api/formField/types";

defineProps<{
  field: FormField;
}>();
</script>

<style scoped lang="scss">
.section-block {
  margin: 8px 0 16px;

  .section-title {
    margin: 0;
    font-size: 20px;
    font-weight: 600;
    line-height: 1.4;
  }

  .section-description {
    margin: 8px 0 0;
    color: #606266;
    line-height: 1.5;
    white-space: pre-wrap;
  }
}
</style>
