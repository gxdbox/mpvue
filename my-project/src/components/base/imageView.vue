<template>
  <div class="image-view" @click="onClick">
    <img
      :class="round ? 'round image' : 'image'"
      :style="{height}"
      :src="src"
      :mode="mode"
      :lazy-load="lazyLoad"
      @load="onLoad"
      @error="onError"
      v-show="!isLoading && !error"
    />
    <img
      :class="round ? 'round image' : 'image'"
      :style="{height}"
      :src="'https://img1.baidu.com/it/u=2015449128,2018423461&fm=253&fmt=auto&app=138&f=JPEG?w=500&h=888'"
      :mode="mode"
      :lazy-load="lazyLoad"
      v-show="isLoading || error"
    />
  </div>
</template>

<script>

export default {
  props: {
    src: {
      type: String,
      default: ''
    },
    mode: {
      type: String,
      default: 'widthFix'
    },
    lazyLoad: {
      type: Boolean,
      default: true
    },
    round: {
      type: Boolean,
      default: false
    },
    height: {
      type: String,
      default: 'auto'
    }
  },
  watch: {
    src(newValue, preValue) {
    }
  },
  data() {
    return {
      isLoading: true,
      error: false
    }
  },
  methods: {
    onClick() {
      this.$emit('onClick')
    },
    onLoad() {
      this.isLoading = false
      this.error = false
      console.log('onLoad')
    },
    onError() {
      this.error = true
      this.isLoading = false
      console.log('onError')
    }
  }
}
</script>

<style lang="scss" scoped>
  .image-view {
    width: 100%;
    .image {
      width: 100%;
      &.round {
        border-radius: 50%;
       }
    }
  }
</style>
