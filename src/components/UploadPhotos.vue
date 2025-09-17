<template>
  <div class="my-5 text-center p-4 rounded-3">
    <h3 class="fw-bold mb-3">Comparte tus fotos</h3>

    <p class="fs-6 mb-3" style="line-height: 1.6; max-width: 650px; margin: 0 auto;">
      Queremos guardar no solo los recuerdos de la boda, sino <strong>toda la experiencia de su estadía</strong>:  
      desde la comida, una caminata en la playa, hasta cualquier momento especial que vivan con nosotros. ✨
    </p>

    <p class="fs-6 mb-4" style="line-height: 1.6; max-width: 650px; margin: 0 auto;">
      Súbelas al álbum con el código <strong>LeifVpn1</strong> o usa el hashtag 
      <strong>#BodaEduardoYKarina</strong> en redes sociales.  
      ¡Nos encantará revivir cada instante a través de sus fotos! 💕
    </p>

    <div class="d-flex flex-column align-items-center">
      <a 
        href="https://web.dotstheapp.com/a?group=1971776&code=LeifVpn1&dlBy=edu.dan68&utm_source=guest&utm_medium=share&utm_campaign=guest_event_album&force_app=1" 
        target="_blank"
        style="text-decoration: none; color: rgb(0, 121, 107);"
      >
        <img 
          :src="qr"
          alt="Código QR del álbum" 
          class="img-fluid mb-3"
          style="max-width: 220px;"
        />
        <div class="fw-bold fs-5">Ir al álbum</div>
      </a>
    </div>
  </div>
</template>

<script setup>
import qr from '../assets/qr.jpg'
</script>
