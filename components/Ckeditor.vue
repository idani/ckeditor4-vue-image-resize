<template>
  <ckEditor
    v-model="contents"
    :editor-url="editorUrl"
    :config="editorConfig"
    @namespaceloaded="onNamespaceLoaded"
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
    return {
      editorUrl: 'https://cdn.ckeditor.com/4.15.1/full-all/ckeditor.js',
      editorConfig: {
        height: this.height,
        extraPlugins: ['image2', 'timestamp'],
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
  },
  methods: {
    onNamespaceLoaded(CKEDITOR) {
      // Add external `placeholder` plugin which will be available for each
      // editor instance on the page.

      let pluginBaseDir = '/ckeditor/plugins/timestamp/'
      if (process.env.NUXT_ENV_DEPLOY_SUBDIR) {
        pluginBaseDir =
          process.env.NUXT_ENV_DEPLOY_SUBDIR + '/ckeditor/plugins/timestamp/'
      }
      CKEDITOR.plugins.addExternal('timestamp', pluginBaseDir, 'plugin.js')
    }
  }
}
</script>

<style scoped></style>
