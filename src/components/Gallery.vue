<template>
  <div class="my-4">
    <h3 class="mb-3 text-center">Galería</h3>
    <div class="container">

      <!-- Imagen principal -->
      <div
        id="carouselImages"
        class="position-relative mx-auto"
        style="max-width: 600px;"
      >
        <img
          :src="imageUrls[selectedIndex]"
          alt="Imagen principal"
          class="d-block w-100 rounded"
          style="max-height: 350px; object-fit: contain;"
        />

        <!-- Botones grandes -->
        <button
          @click="prevImage"
          class="btn btn-dark position-absolute top-50 start-0 translate-middle-y"
          style="opacity: 0.7; width: 45px; height: 45px; border-radius: 50%;"
          aria-label="Anterior"
        >
          <span class="carousel-control-prev-icon"></span>
        </button>

        <button
          @click="nextImage"
          class="btn btn-dark position-absolute top-50 end-0 translate-middle-y"
          style="opacity: 0.7; width: 45px; height: 45px; border-radius: 50%;"
          aria-label="Siguiente"
        >
          <span class="carousel-control-next-icon"></span>
        </button>
      </div>

      <!-- Miniaturas scrollable sin barra -->
      <div
        ref="thumbsContainer"
        class="d-flex flex-nowrap gap-2 mt-3 mx-auto"
        style="max-width: 600px; overflow-x: auto; scroll-behavior: smooth; -webkit-overflow-scrolling: touch; scrollbar-width: none; -ms-overflow-style: none;"
        @wheel.prevent="onWheelScroll"
      >
        <div
          v-for="(img, idx) in imageUrls"
          :key="'thumb-' + idx"
          class="border rounded"
          :class="selectedIndex === idx ? 'border-primary shadow' : 'border-light'"
          style="width: 70px; height: 70px; cursor: pointer; overflow: hidden; flex: 0 0 auto;"
          @click="selectImage(idx)"
        >
          <img
            :src="img"
            alt="Miniatura"
            class="img-fluid h-100 w-100"
            style="object-fit: cover;"
          />
        </div>
      </div>

    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, watch, nextTick } from 'vue'

const selectedIndex = ref(0)
const imageUrls = ref([])

const thumbsContainer = ref(null)
let intervalId = null

function startAutoChange() {
  clearInterval(intervalId)
  intervalId = setInterval(() => {
    nextImage()
  }, 3000)
}

function selectImage(index) {
  selectedIndex.value = index
  startAutoChange() // Reinicia el temporizador al seleccionar manualmente
}

function prevImage() {
  selectedIndex.value = selectedIndex.value === 0 ? imageUrls.value.length - 1 : selectedIndex.value - 1
  startAutoChange()
}

function nextImage() {
  selectedIndex.value = selectedIndex.value === imageUrls.value.length - 1 ? 0 : selectedIndex.value + 1
  startAutoChange()
}

// Cargar imágenes con import.meta.glob
onMounted(() => {
  const images = import.meta.glob('../assets/images/*.{jpg,jpeg,png,gif}', { eager: true })
  imageUrls.value = Object.values(images)
    .map(mod => mod.default || mod)
    .sort()

  startAutoChange()
})

// Centrar miniatura seleccionada en el scroll
watch(selectedIndex, async (newIndex) => {
  await nextTick()
  if (!thumbsContainer.value) return

  const container = thumbsContainer.value
  const thumbElems = container.children
  if (thumbElems.length === 0) return

  const selectedThumb = thumbElems[newIndex]
  const containerRect = container.getBoundingClientRect()
  const thumbRect = selectedThumb.getBoundingClientRect()

  const scrollLeft =
    container.scrollLeft +
    thumbRect.left -
    containerRect.left -
    (container.clientWidth / 2 - thumbRect.width / 2)

  container.scrollTo({ left: scrollLeft, behavior: 'smooth' })
})

// Scroll horizontal con rueda vertical (opcional)
function onWheelScroll(e) {
  if (!thumbsContainer.value) return
  thumbsContainer.value.scrollLeft += e.deltaY
}
</script>

<style scoped>
/* Ocultar scroll en navegadores WebKit */
::-webkit-scrollbar {
  display: none;
}

/* Firefox */
.thumb-container {
  scrollbar-width: none;
}

/* IE, Edge */
.thumb-container {
  -ms-overflow-style: none;
}
</style>
