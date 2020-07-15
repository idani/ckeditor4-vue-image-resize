<template>
  <ckEditor v-model="contents" :config="editorConfig"></ckEditor>
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
      editorConfig: {
        height: this.height
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
