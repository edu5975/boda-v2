<template>
  <div class="app-background">
    <div
      class="container py-4 text-center"
      style="font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; color: #004d40;"
    >
      <Header />
      <MusicPlayer />
      <Countdown />
      <Gallery />
      <LocationMaps/>
      <Itinerary />
      <GiftList />
      <DressCode />
      <UploadPhotos />
      <ThankYou />
    </div>
    <Footer />
  </div>
</template>

<script setup>
import Header from './components/Header.vue'
import MusicPlayer from './components/MusicPlayer.vue'
import Countdown from './components/Countdown.vue'
import Gallery from './components/Gallery.vue'
import Itinerary from './components/Itinerary.vue'
import GiftList from './components/GiftList.vue'
import DressCode from './components/DressCode.vue'
import UploadPhotos from './components/UploadPhotos.vue'
import ThankYou from './components/ThankYou.vue'
import LocationMaps from './components/LocationMaps.vue'
import Footer from './components/Footer.vue'
</script>

<style>

.app-background {
  background-image: url('/src/assets/background.png');
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  background-attachment: fixed;
  min-height: 100vh;
  width: 100%;
}
</style>
