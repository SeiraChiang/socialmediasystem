<template>
    <div id="timebox">{{ currentTime }}</div>
</template>
  
<script setup lang="ts">
import { ref, onMounted } from 'vue';

const currentTime = ref('');

const updateCurrentTime = () => {
    const nowDate = new Date();
    currentTime.value = nowDate.toUTCString();
};

onMounted(() => {
    updateCurrentTime();
    // setInterval(updateCurrentTime, 1000);
});
</script>

<style scoped>
#timebox{
    font-size: 8px;
}
</style>
  
  