<template>
  <input
    v-model="keyword"
    type="text"
    placeholder="Search for awesome gifs."
    @input="onInput"
  />
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      keyword: "",
      timeout: null
    };
  },
  methods: {
    onInput() {
      clearTimeout(this.timeout)
      this.timeout = setTimeout(()=> this.search(),500)
    },
    async search() {
      const res = await fetch(
        `https://api.giphy.com/v1/gifs/search?api_key=YOUR_API_KEY&q=${this.keyword}&limit=12`
      );
      const data = await res.json();
      this.$emit("fetch-gifs", data.data)
    },
  },
};
</script>

<style scoped>
input {
  padding: 10px 16px;
  border-radius: 4px;
  font-size: 18px;
  outline: 0;
  border: 2px solid gray;
  width: 100%;
  display: block;
}

input:focus {
  border-color: dodgerblue;
}
</style>
