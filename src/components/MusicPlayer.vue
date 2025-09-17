<template>
<div class="my-5 rounded-3 text-center">
    <h3 class="fw-bold mb-2" style="letter-spacing: 1px;">Nuestra canción</h3>
    <br>
    <audio
      controls
      :autoplay="autoplayEnabled"
      :src="song"
      style="width: 100%; max-width: 400px"
    ></audio>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import song from '../assets/song.mp3'

// Puedes controlar esta variable desde el script o el padre del componente
const autoplayEnabled = ref(true)
</script>
