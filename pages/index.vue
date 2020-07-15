<template>
  <v-layout column justify-center align-center>
    <v-flex xs12 sm8 md6>
      <div class="text-center">
        <logo />
        <vuetify-logo />
      </div>
      <v-card>
        <v-card-title class="headline">
          CKEditor4-vue image resize example
        </v-card-title>
        <v-card-text>
          <ckeditor v-model="contents" :height="height" />
        </v-card-text>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
import Logo from '~/components/Logo.vue'
import VuetifyLogo from '~/components/VuetifyLogo.vue'
import Ckeditor from '~/components/Ckeditor'

export default {
  components: {
    Logo,
    VuetifyLogo,
    Ckeditor
  },
  data: () => ({
    contents: '',
    height: 500
  })
}
</script>
