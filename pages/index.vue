<template>
  <div>
    <client-only>
      <Editor :value="value" :toolbarItems="[]" :plugins="enabledPlugins" @change="handleChange"/>
    </client-only>
  </div>
</template>

<script>
import {Editor, Viewer} from '@bytemd/vue';
import gfm from '@bytemd/plugin-gfm';
import highlight from '@bytemd/plugin-highlight-ssr';
import mermaid from '@bytemd/plugin-mermaid';
import math from '@bytemd/plugin-math-ssr';
import footnotes from '@bytemd/plugin-footnotes';


export default {
  name: "drafts",
  components: {Editor},
  data() {
    return {
      value: ''
    };
  },
  computed: {
    enabledPlugins() {
      return [
        gfm(),
        highlight(),
        mermaid(),
        math(),
        footnotes()
      ];
    },
  },
  methods: {
    handleChange(v) {
      this.value = v;
    },
  },
};
</script>

<style>
.bytemd {
  height: 100vh !important;
}
.bytemd .bytemd-toolbar {
  display: none;
}
</style>
