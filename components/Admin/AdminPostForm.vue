<template>
  <form @submit.prevent="onSave">
    <AppControlInput v-model="editedPost.author">Author Name</AppControlInput>

    <AppControlInput v-model="editedPost.title">Title</AppControlInput>
            
    <AppControlInput v-model="editedPost.thumbnail">Thumbnail Link</AppControlInput>
            
    <AppControlInput
              control-type="textarea"
              v-model="editedPost.previewText">Preview Text</AppControlInput>

    <AppControlInput
              control-type="textarea"
              v-model="editedPost.content">Content</AppControlInput>
            
    <AppButton type="submit">Save</AppButton>
            
    <AppButton
              type="button"
              style="margin-left: 10px"
              btn-style="cancel"
              @click="onCancel">Cancel</AppButton>
  </form>
</template>

<script>
import AppControlInput from '@/components/UI/AppControlInput'
import AppButton from '@/components/UI/AppButton'
export default {
  components:{
    AppControlInput,
    AppButton
  },
  props: {
    post : {
      type: Object,
      required: false
    }
  },
  data() {
    return {
      editedPost : this.post ? {...this.post} : {
        author: '',
        title: '',
        content: '',
        previewText: '',
        thumbnail: ''
      }
    }
  },
  methods: {
    onSave() {
      console.log('====54====this.editedPost======' + JSON.stringify(this.editedPost))
      this.$emit('submit', this.editedPost)
    },
    onCancel() {
      this.$router.push('/admin')
    }
  }
}
</script>
