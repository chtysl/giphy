<template>
  <div class="gif" :style="`background-image: url('${gif.images.original.url}')`">
    <input ref="url"  readonly type="text" style="flex: 1" :value="gif.images.original.url">
    <button @click="copy()">Copy</button>
  </div>
</template>

<script>
export default {
  name: "SearchedGif",
  props: ['gif'],
  data() {
    return {
      url : ''
    }
  },
  methods: {
    copy() {
      this.$refs.url.select();
      this.$refs.url.setSelectionRange(0, 99999); /*For mobile devices*/

      document.execCommand("copy");
      this.$refs.url.value = 'Copied!!!';
    }
  }
}
</script>

<style scoped>
.gif {
  width: 240px;
  height: 240px;
  margin-bottom: 20px;
  display: inline-flex;
  justify-content: center;
  align-items: flex-end;
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
</style>
