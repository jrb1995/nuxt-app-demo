<template>
  <div id="web-editor">
    <header class="header">
      <div class="header-content">
        logo
      </div>
    </header>

    <textarea ref="textarea" placeholder="输入标题..." spellcheck="false" maxlength="80" rows="1" class="title-input" @input="handleChange"></textarea>
    <div 
      class="quill-editor" 
      :content="content"
      @change="onEditorChange($event)"
      @blur="onEditorBlur($event)"
      @focus="onEditorFocus($event)"
      @ready="onEditorReady($event)"
      v-quill:myQuillEditor="editorOption">
    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        content: '',
        editorOption: {
          // some quill options
          placeholder: '输入正文...',
          modules: {
            toolbar: [
              ['bold', 'italic', 'underline', 'strike', 'blockquote', 'code-block']
            ],
          }
        }
      }
    },
    mounted() {
      console.log('app init, my quill insrance object is:', this.myQuillEditor)
    },
    methods: {
      onEditorBlur(editor) {
        console.log('editor blur!', editor)
      },
      onEditorFocus(editor) {
        console.log('editor focus!', editor)
      },
      onEditorReady(editor) {
        console.log('editor ready!', editor)
      },
      onEditorChange({ editor, html, text }) {
        console.log('editor change!', editor, html, text)
        this.content = html
      },
      handleChange (e) {
        this.$refs.textarea.style.height = 'auto';
        this.$refs.textarea.style.height = this.$refs.textarea.scrollHeight + 'px';
      }
    }
  }
</script>

<style scoped>
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  padding: 0 16px;
  height: 64px;
  background-color: #fff;
  border-bottom: none;
  z-index: 100;
}

.header-content {
  display: flex;
  align-items: center;
  margin: 0 auto;
  width: 1000px;
  max-width: 100%;
  height: 100%;
}

.title-input {
  margin: 0;
  padding: 0;
  line-height: 36px;
  font-size: 32px;
  font-weight: 700;
  color: #000;
  border: none;
  outline: none;
  resize: none;
  overflow: hidden;
  width: 100%;

  padding-top: 144px;

  padding-left: calc(50% - 345px);
  padding-right: calc(50% - 345px);
}
</style>

<style>
html {
  color: #333;
  font-family: -apple-system,system-ui,BlinkMacSystemFont,Helvetica Neue,PingFang SC,Hiragino Sans GB,Microsoft YaHei,Arial,sans-serif;
}

.ql-toolbar.ql-snow {
  position: fixed;
  top: 64px;
  width: 100%;
  user-select: none;
  z-index: 50;
  border: none;
  border-bottom: 1px solid #f7f7f7;
  background-color: #fff;
  /* padding: 0; */
  /* font-family: Helvetica Neue,Helvetica,Arial,sans-serif; */
}

.ql-toolbar.ql-snow .ql-formats {
  display: block;
  margin: 0 auto;
  padding: 0;
  width: 700px;
  max-width: 100%;
}

.quill-editor {
  padding-top: 36px;
  padding-left: calc(50% - 345px);
  padding-right: calc(50% - 345px);
  font-family: -apple-system,system-ui,BlinkMacSystemFont,Helvetica Neue,PingFang SC,Hiragino Sans GB,Microsoft YaHei,Arial,sans-serif;
}

.ql-editor {
  padding: 0;
  position: relative;
  font-size: 16px;
  line-height: 1.6;
  word-break: break-word;
}

.ql-container.ql-snow {
  border: none;
}

.ql-editor.ql-blank::before {
  left: 0;
  right: 0;
  font-style: normal;
  color: #b3b3b1;
}
</style>