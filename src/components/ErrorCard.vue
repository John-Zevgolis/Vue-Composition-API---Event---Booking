<template>
  <SectionCard>
    <div class="space-x-4 flex items-center flex-col">
      <div class="text-red-500">
        <slot></slot>
      </div>
      <RoundButton v-if="retry" @click="retry">Retry now</RoundButton>
    </div>
  </SectionCard>
</template>

<script setup>
import SectionCard from '@/components/SectionCard.vue';
import RoundButton from '@/components/RoundButton.vue';

defineProps({
  retry: {
    type: Function,
  },
});
</script>
