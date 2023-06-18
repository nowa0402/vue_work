<template>
  <v-col cols="auto">
    <v-btn rounded="sm" :icon="props.iconName" :disabled="isDisable" @click="onclick"></v-btn>
  </v-col>
</template>

<script setup lang="ts">
import { computed } from 'vue'

const props = defineProps({
  iconName: String,
  nowCount: Number,
  maxCount: Number,
  step: Number,
})

const isDisable = computed(() => {
  return Number(props.nowCount) === Number(props.maxCount) ? true : false
})

const emit = defineEmits<{
  countPlus: [step: number]
}>()

const onclick = () => {
  emit('countPlus', Number(props.step))
}
</script>
