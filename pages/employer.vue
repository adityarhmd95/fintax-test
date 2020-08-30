<template>
  <div class="wrapEmployer">
    <h1>List Employer</h1>
    <TableEmployer />
  </div>
</template>

<script>
  import TableEmployer from '~/components/TableEmployer'
  export default {
    components: {
      TableEmployer
    }
  }
</script>

<style lang="scss" scoped>
  .wrapEmployer {
    width: 100%;
    display: flex;
    flex-flow: column;
  }
</style>