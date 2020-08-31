<template>
  <div class="table">
    <div class="tRow tHead">
      <div class="item name" @click="sortAlphabet">
        Name
        <img src="~/assets/caret-down.svg" width="12" :class="{caretUp : sortOrder == 'desc'}">
      </div>
      <div class="item">Age</div>
      <div class="item">Salary</div>
    </div>
    <div class="tRow tBody" 
      v-for="(employer, index) in dataEmployers" 
      :key="index" 
      :class="{oddRow : index%2 != 0}">
      <div class="item" @click="storeData(employer)">{{employer.employee_name}}</div>
      <div class="item">{{employer.employee_age}}</div>
      <div class="item">{{employer.employee_salary | currency}}</div>
    </div>
    <div class="totalRecord">Total records: {{dataEmployers.length}}</div>
    <span class="hint">(Click employer name to view detail)</span>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        sortOrder: 'asc'
      }
    },
    props: ['dataEmployers'],
    methods: {
      sortAlphabet() {
        if(this.sortOrder == 'asc') {
          this.sortOrder = 'desc'
          this.$emit('sortAlphabet', 'desc')
        } else {
          this.sortOrder = 'asc'
          this.$emit('sortAlphabet', 'asc')
        }
      },
      storeData(data) {
        localStorage.dataEmployer = JSON.stringify(data)
        this.$router.push('/employer')
      }
    }
  }

</script>

<style lang="scss" scoped>
  .table {
    display: flex;
    flex-flow: column;

    .tRow {
      display: flex;
      flex-flow: row;
      height: 35px;
      align-items: center;

      &.tHead {
        height: 50px;
        background: #3E7DC0;
        color: #FFFFFF;

        .name {
          cursor: pointer;

          .caretUp {
            transform: rotate(180deg);
          }
        }
      }

      &.oddRow {
        background: #e2f0ff;
      }

      .item {
        width: 25%;
        padding: 0 15px;

        &:first-child {
          width: 50%;
          cursor: pointer;
        }
      }
    }

    .totalRecord {
      font-size: 15px;
      margin-top: 10px;
      margin-bottom: 10px;
    }
  }

</style>
