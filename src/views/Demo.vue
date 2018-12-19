<template>
  <div class="quill-wrap">
    <quill-editor
      v-model="content"
      ref="myQuillEditor"
      :options="editorOption"
    >
    </quill-editor>
  </div>
</template>
<script>
  import {quillEditor, Quill} from 'vue-quill-editor'
  import {container, ImageExtend, QuillWatch} from 'quill-image-extend-module'

  Quill.register('modules/ImageExtend', ImageExtend)
  export default {
    components: {quillEditor},
    data() {
      return {
       content: 'asdasdada',
        // 富文本框参数设置
        editorOption: {  
          modules: {
            ImageExtend: {
              loading: true,
              name: 'img',
              action: 'asdadasd',
              response: (res) => {
                return res.info
              }
            },
            toolbar: {
              container: container,
              handlers: {
                'image': function () {
                  QuillWatch.emit(this.quill.id)
                }
              }
            }
          }
        }
      }
    }
  }
</script>