<template>
  <div class="my-5 rounded-3 text-center">
    <h3 class="fw-bold mb-2" style="letter-spacing: 1px;">Cuenta regresiva</h3>
    <div class="row justify-content-center g-3">
      <div
        class="col-6 col-md-auto d-flex justify-content-center"
        v-for="(unit, label) in countdown"
        :key="label"
      >
        <div class="time-card">
          <div class="time-content">
            <div class="time-value">{{ unit }}</div>
            <div class="time-label">{{ label }}</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'

const countdown = ref({
  Días: '0',
  Horas: '0',
  Min: '0',
  Seg: '0'
})

const eventDate = new Date('2025-10-24T13:15:00')

function updateCountdown() {
  const now = new Date()
  const diff = eventDate - now

  if (diff <= 0) {
    countdown.value = {
      Días: '0',
      Horas: '0',
      Min: '0',
      Seg: '0'
    }
    return
  }

  countdown.value.Días = Math.floor(diff / (1000 * 60 * 60 * 24))
  countdown.value.Horas = Math.floor((diff / (1000 * 60 * 60)) % 24)
  countdown.value.Min = Math.floor((diff / (1000 * 60)) % 60)
  countdown.value.Seg = Math.floor((diff / 1000) % 60)
}

let interval

onMounted(() => {
  updateCountdown()
  interval = setInterval(updateCountdown, 1000)
})

onBeforeUnmount(() => {
  clearInterval(interval)
})
</script>

<style scoped>
.time-card {
  width: 120px;
  height: 120px;
  background-color: #ffffff;
  border-radius: 1rem;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.08);
  display: flex;
  align-items: center;
  justify-content: center;
}

.time-content {
  text-align: center;
}

.time-value {
  font-size: 2.2rem;
  font-weight: bold;
  color: #00796b;
  line-height: 1;
}

.time-label {
  font-size: 1rem;
  color: #555;
  margin-top: 4px;
}
</style>
