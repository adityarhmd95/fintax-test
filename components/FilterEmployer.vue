<template>
  <div class="wrapFilter">
    <select v-model="filterShow">
      <option value="3">3</option>
      <option value="5">5</option>
      <option value="10">10</option>
      <option value="all">Show All</option>
    </select>
  </div>
</template>

<script>
export default {
  data() {
    return {
      filterShow: 'all'
    }
  },
  watch: {
    filterShow(newVal) {
      this.$emit('filterTotal', newVal)
      localStorage.filter = newVal; //implement local storage
    }
  }
}
</script>

<style lang="scss" scoped>
  .wrapFilter {
    width: 100%;
    display: flex;
    flex-flow: column;
    align-items: flex-end;
    margin: 15px 0;

    select {
      width: 130px;
      height: 40px;
      border-radius: 5px;
      padding: 0 10px;
      border: 1px solid #AAA;
      font-family: 'Roboto';
    }
  }
</style>