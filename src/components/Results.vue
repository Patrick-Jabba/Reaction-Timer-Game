<script setup>
  const props = defineProps({
    results: Number
  })
</script>

<template>
  <h2>
    Reaction Time: {{ results }}ms
  </h2>

  <div v-if="props.results < 300">
    <h3>Você é veloz como um Cheetah!!!</h3>
    <img src="https://www.thoughtco.com/thmb/VOFTSp8g3fh7qN4SiQxQNeSupFo=/1500x0/filters:no_upscale():max_bytes(150000):strip_icc()/front-view-of-a-female-cheetah--acinonyx-jubatus--running-73553651-5c62c0a2c9e77c0001566d2a.jpg" alt="">
  </div>
  <div v-if="props.results >= 400">
    <h3>Reflexo de Tartaruga.</h3>
    <img src="https://aventurasnahistoria.uol.com.br/media/uploads/personagem/jonathan_tartaruga.jpg" alt="">
  </div>
  <div v-if="props.results >= 300 && props.results < 400">
    <h3>Nos saltos da Lebre!</h3>
    <img src="https://www.infoescola.com/wp-content/uploads/2018/03/lebre_172352939.jpg" alt="">
  </div>
</template>

<style scoped>
img {
  width: 200px;
  border-radius: 4px;
}
</style>