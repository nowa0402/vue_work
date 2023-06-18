<template>
  <v-col cols="auto">
    <v-btn rounded="sm" :icon="props.iconName" v-on:click="onclick"></v-btn>
  </v-col>
</template>

<script setup lang="ts">
const props = defineProps({
  iconName: String,
  active: Boolean,
})

const emit = defineEmits<{
  activeChange: [active: boolean]
}>()

const onclick = () => {
  emit('activeChange', props.active)
}
</script>
