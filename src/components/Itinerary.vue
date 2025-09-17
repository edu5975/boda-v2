<template>
  <div class="my-5 rounded-3 text-center">
    <h3 class="fw-bold mb-2" style="letter-spacing: 1px;">Itinerario del Evento</h3>
    <div class="d-flex flex-column gap-3 mx-auto" style="max-width: 400px;">
      <div
        v-for="(item, index) in itinerary"
        :key="index"
        class="d-flex align-items-center p-3 rounded shadow-sm"
        style="background: #fff;"
      >
        <div
          class="d-flex align-items-center justify-content-center rounded-3 border me-3"
          style="width: 70px; height: 50px; font-size: 1rem; font-weight: 600;"
          aria-label="Hora"
        >
          {{ item.time }}
        </div>

        <div class="text-start">
          <h5 class="mb-1 fw-semibold">{{ item.description }}</h5>
          <small class="text-muted">{{ item.location }}</small>
        </div>
      </div>
    </div>
  </div>
</template>


<script setup>
import { ref } from 'vue'

const itinerary = ref([
  {
    time: '1:15 pm',
    description: 'Misa',
    location: 'Templo de Nuestra Señora de Guadalupe',
  },
  {
    time: '4:00 pm',
    description: 'Cóctel',
    location: 'Hotel Sunscape',
  },
  {
    time: '5:00 pm',
    description: 'Recepción',
    location: 'Hotel Sunscape',
  },
  {
    time: '6:00 pm',
    description: 'Fiesta',
    location: 'Hotel Sunscape',
  },
])
</script>
