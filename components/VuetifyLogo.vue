<template>
  <img class="VuetifyLogo" alt="Vuetify Logo" :src="vuetifyLogPath" />
</template>

<script>
export default {
  name: 'VuetifyLogo',
  data() {
    let vuetifyLogPath = '/vuetify-logo.svg'
    if (process.env.NUXT_ENV_DEPLOY_SUBDIR) {
      vuetifyLogPath = process.env.NUXT_ENV_DEPLOY_SUBDIR + 'vuetify-logo.svg'
    }
    return {
      vuetifyLogPath
    }
  }
}
</script>

<style>
.VuetifyLogo {
  height: 180px;
  width: 180px;
  transform: rotateY(560deg);
  animation: turn 3.5s ease-out forwards 1s;
}

@keyframes turn {
  100% {
    transform: rotateY(0deg);
  }
}
</style>
