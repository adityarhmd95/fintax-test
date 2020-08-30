<template>
  <div class="table">
    <div class="tRow tHead">
      <div class="item">Name</div>
      <div class="item">Age</div>
      <div class="item">Salary</div>
    </div>
    <div class="tRow tBody" 
      v-for="(employer, index) in dataEmployers" 
      :key="index" 
      :class="{oddRow : index%2 != 0}">
      <div class="item">{{employer.employee_name}}</div>
      <div class="item">{{employer.employee_age}}</div>
      <div class="item">{{employer.employee_salary}}</div>
    </div>
  </div>
</template>

<script>
  export default {
    props: ['dataEmployers']
  }

</script>

<style lang="scss" scoped>
  .table {
    display: flex;
    flex-flow: column;
    max-width: 500px;

    .tRow {
      display: flex;
      flex-flow: row;
      height: 30px;
      align-items: center;

      &.tHead {
        background: #3E7DC0;
        color: #FFFFFF;
      }

      &.oddRow {
        background: #e2f0ff;
      }

      .item {
        width: 25%;
        padding: 0 15px;

        &:first-child {
          width: 50%;
        }
      }
    }
  }

</style>
