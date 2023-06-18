<template>
  <v-row>
    <counter-btn v-bind="backCountOption" @count-plus="countUpDown"></counter-btn>
    <active-btn :icon-name="activeIcon" :active="playActive" @active-change="changeActive" />
    <counter-btn v-bind="forwardCountOption" @count-plus="countUpDown"></counter-btn>
  </v-row>
</template>

<script setup lang="ts">
import ActiveBtn from './date_btn/ActiveBtn.vue'
import CounterBtn from './date_btn/CounterBtn.vue'
import { ref, computed, reactive } from 'vue'

const iconNames = {
  active: {
    play: 'mdi-play',
    stop: 'mdi-stop',
  },
  backward: 'mdi-step-backward-2',
  forward: 'mdi-step-forward-2',
}

const playActive = ref(true)
const activeIcon = computed(() => {
  return playActive.value ? iconNames.active.stop : iconNames.active.play
})
const changeActive = (event: boolean) => {
  playActive.value = !event
}

const nowCount = ref(0)
const countUpDown = (event: number) => {
  nowCount.value += event
}

const backCountOption = reactive({
  iconName: iconNames.backward,
  maxCount: -10,
  nowCount: nowCount,
  step: -1,
})
const forwardCountOption = reactive({
  iconName: iconNames.forward,
  maxCount: 10,
  nowCount: nowCount,
  step: 1,
})
</script>
