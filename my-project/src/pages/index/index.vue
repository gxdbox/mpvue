<template>
  <div>
    <div class="search-bar">首页搜索框组建</div>
    <div>
      <SearchBar
        :disabled="true"
        @click="onSearchBarKClick"/>
    </div>
    <div>
      <ImageView
        src="https://t7.baidu.com/it/u=1819248061,230866778&fm=193&f=GIF"
        height="300px"
        mode="scaleToFill"
      />
    </div>
  </div>
</template>

<script>
import SearchBar from '../../components/home/SearchBar'
import ImageView from '../../components/base/imageView.vue'

export default {
  components: {ImageView, SearchBar},
  methods: {
    onSearchBarKClick() {}
  }

}
</script>

<style lang="css" scoped>
  .msg {
    color : red;
    font-size: 20px;
    font-weight: bold;
  }

</style>
