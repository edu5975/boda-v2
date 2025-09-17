<template>
  <div class="mt-3">
    <label class="lead form-label fw-bold">Nuestra canción</label>
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
