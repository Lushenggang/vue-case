<template>
  <div class="editor">
  </div>
</template>

<script>
import * as monaco from 'monaco-editor'
import 'monaco-editor/esm/vs/editor/contrib/clipboard/clipboard.js'

self.MonacoEnvironment = {
  getWorkerUrl: function (moduleId, label) {
    if (label === 'json') {
      return './json.worker.bundle.js';
    }
    if (label === 'css') {
      return './css.worker.bundle.js';
    }
    if (label === 'html') {
      return './html.worker.bundle.js';
    }
    if (label === 'typescript' || label === 'javascript') {
      return './ts.worker.bundle.js';
    }
    return './editor.worker.bundle.js';
  }
}

export default {
  data () {
    return {}
  },
  mounted () {
    let editor = monaco.editor.create(this.$el, {
      value: 'console.log("Helloworld")',
      language: 'javascript'
    })
    editor.layout({
      width: 1000,
      height: 400
    })
  }
}
</script>

<style lang="stylus">
.monaco-editor
  text-align left
  box-shadow 0 0 1px 1px #3361D8
</style>
