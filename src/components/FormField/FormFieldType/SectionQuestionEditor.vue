<template>
  <div class="section-box">
    <el-input class="section-title" :model-value="props.field.label" @update:model-value="handleTitleInput"
      @blur="handleCommit" placeholder="標題" />

    <el-input class="section-description" :model-value="props.field.description"
      @update:model-value="handleDescriptionInput" @blur="handleCommit" type="textarea" autosize placeholder="說明" />
  </div>

  <QuestionFooter :index="props.index" :total="props.total" :is-required="0" :show-required="false"
    @delete="emit('delete')" @copy="emit('copy')" @move-up="emit('move-up')" @move-down="emit('move-down')" />
</template>

<script setup lang="ts">
import type { FormField, QuestionEditorBaseEmits } from "@/api/formField/types";
import QuestionFooter from "@/components/FormField/FormFieldCommon/QuestionFooter.vue";

const props = defineProps<{
  field: FormField;
  index: number;
  total: number;
}>();

const emit = defineEmits<QuestionEditorBaseEmits>();

const handleTitleInput = (value: string) => {
  emit("update-local", { label: value });
};

const handleDescriptionInput = (value: string) => {
  emit("update-local", { description: value });
};

const handleCommit = () => {
  emit("commit");
};
</script>

<style lang="scss" scoped>
.section-box {
  margin: 2% 0 5%;

  .section-title {
    margin-bottom: 10px;

    :deep(.el-input__wrapper) {
      box-shadow: 0 1px 0 0 #ccc;
      border-radius: 0;
    }
  }

  .section-description {
    :deep(.el-textarea__inner) {
      box-shadow: 0 1px 0 0 #ccc;
      border-radius: 0;
      min-height: 40px;
    }
  }
}
</style>
