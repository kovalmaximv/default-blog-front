<template>
  <div>
    <div style="height: 30px;"/>
    <textarea v-if="!preview" :value="input" @input="update"/>
    <div v-else v-html="compiledMarkdown" class="editor-class" style="font-size:18px"/>

    <div style="height: 10px"/>

    <table>
        <tr>
            <td style="text-align: left;">
                <button v-on:click="previewMode">Превью</button>
            </td>
            <td style="text-align: right;">
                <button v-if="preview" v-on:click="createPost">Добавить пост</button>
            </td>
        </tr>
    </table>
    
    <div style="height: 30px;"/>

    <input v-model.number="postId" v-on:keyup.enter="getPost"/>
  </div>
</template>

<script>
import axios from 'axios'
import marked from 'marked'
import _ from 'lodash'
import DOMPurify from 'dompurify'

export default {
  name: 'HelloWorld',
  data() {
    return {
      input: '# hello',
      postId: null,
      preview: false
    }
  },
  computed: {
    compiledMarkdown() {
      return DOMPurify.sanitize(marked(this.input));
    }
  },
  methods: {
    update: _.debounce(function(e) {
      console.log(e.target.value)
      this.input = e.target.value;
    }, 300),

    createPost: function() {
      axios({
        method: 'post',
        url: 'http://localhost:8080/api/v1/posts',
        data: {
          content: this.input
        }
      })
    },

    previewMode: function() {
      this.preview = !this.preview;
    },

    getPost: function() {
      axios({
        method: 'get',
        url: `http://localhost:8080/api/v1/posts/${this.postId}`
      }).then(result => {
        this.input = result.data.content
      })
    }
  }
}
</script>

<style>
html,
body {
  margin: 0;
  height: 100%;
  font-family: "Monaco", courier, monospace;
  color: #333;
  background-color: #f6f6f6;
}

textarea {
  display: inline-block;
  width: 49%;
  height: 100%;
  vertical-align: top;
  box-sizing: border-box;
  height: 450px;
  border: none;
  border-radius: 8px;
  resize: none;
  outline: none;
  font-size: 18px;
  font-family: "Monaco", courier, monospace;
  padding: 20px;
}

.editor-class {
  display: inline-block;
  width: 49%;
  height: 100%;
  vertical-align: top;
  box-sizing: border-box;
  height: 450px;
  border: none;
  border-radius: 8px;
  outline: none;
  font-family: "Monaco", courier, monospace;
  padding: 20px;
  background-color: white;
}

table {
  display: inline-table;
  width: 49%;
  height: 100%;
  vertical-align: top;
  box-sizing: border-box;
  padding: 0 20px;
}

button {
    border:none;
    border-radius: 4px;
    background-color: #242c42;
    color:white;
    font-size: 18px;
    display: inline-block;
    text-align: center;
    text-decoration: none;
    padding: 5px 10px;
    margin-left: 30px;
    margin-right: 30px;
}
</style>
