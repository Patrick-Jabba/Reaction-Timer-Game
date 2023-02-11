<script setup>
  import { onMounted, reactive } from "vue";

  const state = reactive({
    showBlock: false,
    timer: null,
    reactionTime: 0,
  });

  const props = defineProps({
    delay: Number
  });

  const emits = defineEmits([''])

  onMounted(() => {
    setTimeout(() => {
      state.showBlock = true
      startTimer();
    }, props.delay)
  });

  function startTimer() {
    state.timer = setInterval(() => {
      state.reactionTime += 10
    }, 10);
  };

  function stopTimer() {
    clearInterval(state.timer);
    emits('end', state.reactionTime)
  }

</script>

<template>
  <div class="block" v-if="state.showBlock" @click="stopTimer">
    CLICK ME FAST!!!  
  </div>  
</template>

<style scoped>
  .block {
    width: 400px;
    border-radius: 20px;
    background-color: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
  }
</style>