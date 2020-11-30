<template>
  <ckEditor
    v-model="contents"
    :editor-url="editorUrl"
    :config="editorConfig"
  ></ckEditor>
</template>

<script>
import CKEditor from 'ckeditor4-vue'
export default {
  name: 'CKEditor4',
  components: { ckEditor: CKEditor.component },
  props: {
    value: {
      type: String,
      required: true
    },
    height: {
      type: Number,
      required: false,
      default: 500
    }
  },
  data() {
    // let ckeditorbaseDir = '/ckeditor/ckeditor.js'
    // if (process.env.NUXT_ENV_DEPLOY_SUBDIR) {
    //   ckeditorbaseDir =
    //     process.env.NUXT_ENV_DEPLOY_SUBDIR + 'ckeditor/ckeditor.js'
    // }
    return {
      editorUrl: 'https://cdn.ckeditor.com/4.15.1/full-all/ckeditor.js',
      editorConfig: {
        height: this.height,
        extraPlugins: ['image2'],
        removePlugins: ['image']
      }
    }
  },
  computed: {
    contents: {
      get() {
        return this.value
      },
      set(value) {
        this.$emit('input', value)
      }
    }
  }
}
</script>

<style scoped></style>
