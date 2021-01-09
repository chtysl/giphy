<template>
  <search @fetch-gifs="onFetch" />
  <gif-list :gifs="gifs" />
</template>

<script>
import Search from "@/components/Search";
import GifList from "@/components/GifList";
export default {
  components: {
    GifList,
    Search,
  },
  data() {
    return {
      gifs: [],
    };
  },
  methods:{
    onFetch(result){
      this.gifs = result
    }
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}
body {
  padding: 50px;
}
</style>
