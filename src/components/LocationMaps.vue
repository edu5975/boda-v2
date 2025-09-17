<template>
  <div class="my-5 rounded-3 text-center">
    <h3 class="fw-bold mb-2" style="letter-spacing: 1px;">Ubicación</h3>

    <div class="row g-4 justify-content-center">
      <!-- Mapa del Templo -->
      <div class="col-12 col-md-6">
        <h5 class="text-center mb-2">Templo</h5>
        <div class="ratio ratio-16x9 rounded shadow">
          <iframe
            :src="templeMapUrl"
            style="border:0;"
            allowfullscreen=""
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
          ></iframe>
        </div>
      </div>

      <!-- Mapa del Hotel -->
      <div class="col-12 col-md-6">
        <h5 class="text-center mb-2">Salón de Fiestas</h5>
        <div class="ratio ratio-16x9 rounded shadow">
          <iframe
            :src="hotelMapUrl"
            style="border:0;"
            allowfullscreen=""
            loading="lazy"
            referrerpolicy="no-referrer-when-downgrade"
          ></iframe>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const templeMapUrl = `https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3734.506565496604!2d-105.23468199999999!3d20.608198999999995!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8421454ee558359d%3A0xf136b7cb80ca3b3b!2sParroquia%20de%20Nuestra%20Se%C3%B1ora%20de%20Guadalupe!5e0!3m2!1ses!2smx!4v1749508708609!5m2!1ses!2smx`
const hotelMapUrl = `https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3733.6702393335245!2d-105.24127132390555!3d20.64229388091224!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x842145bf5038d23f%3A0x7b0192fcd13ef2c0!2sSunscape%20Puerto%20Vallarta%20Resort%20%26%20Spa!5e0!3m2!1ses!2smx!4v1749508774484!5m2!1ses!2smx`
</script>
