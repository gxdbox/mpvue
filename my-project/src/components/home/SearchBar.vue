<template>
  <div class="search-bar">
    <div class="search-bar-wrapper">
      <van-icon
        class="search"
        name="search"
        size="16px"
        color="#858C96"/>
      <input class="search-bar-input"
      :focus="focus"
      :disabled="disabled"
       :maxlength="limit"
      :placeholder="hostSearch.length === 0 ?'请输入搜索关键字' : hostSearch"
      v-model="searchWord"
      @click="onChange"
      confirm-type="search"
      @confirm="onConfirm"
      placeholder-style="color: #ADB4BE"/>
      <van-icon
        class="clear"
        name="clear"
        size="16px"
        color="#858C96"
        @click="onClearClick"
        v-if="searchWord.length > 0"/>

    </div>
  </div>

</template>

<script>

export default {
  props: {
    focus: {
      type: Boolean,
      default: true
    },
    disabled: {
      type: Boolean,
      default: false
    },
    limit: {
      type: Number,
      default: 50
    },
    hostSearch: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      searchWord: ''
    }
  },
  methods: {
    onSearchBarClick() {
      this.$emit('onClick')
    },
    onClearClick() {
      this.searchWord = ''
      this.$emit('onClear')
    },
    onChange(e) {
      const {value} = e.mp.detail
      this.$emit('onChange', value)
    },
    onConfirm(e) {
      const {value} = e.mp.detail
      this.$emit('onConfirm', value)
    },
    setValue(v) {
      this.searchWord = v
    },
    getValue() {
      return this.searchWord
    }
  }
}
</script>

<style lang="css" scoped>
  .search-bar {
    padding: 10px 15px;
    height: 40px;
  }
  .search-bar-wrapper {
    display: flex;
    align-items: center;
    background: beige;
    padding: 12px 17px;
    height: 40px;
    box-sizing: border-box;
  }
  .search-bar-input {
    flex: 1;
    margin: 0 8px;
  }
  .search, .clear {
    display: flex;
    align-items: center;
    height: 100%;
  }
</style>
