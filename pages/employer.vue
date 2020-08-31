<template>
  <div class="wrapEmployer">
    <nuxt-link class="btnBack" to="/">Back</nuxt-link>
    <h1>Employer Detail</h1>
    <div class="detail" v-if="dataEmployer">
      <div class="items">
        <div class="key">Employer Name</div>
        <div class="value">: {{dataEmployer.employee_name}}</div>
      </div>
      <div class="items">
        <div class="key">Employer Age</div>
        <div class="value">: {{dataEmployer.employee_age}}</div>
      </div>
      <div class="items">
        <div class="key">Employer Salary</div>
        <div class="value">: {{dataEmployer.employee_salary | currency}}</div>
      </div>
    </div>
    <span class="hint">(this data is obtained through Local storage)</span>
  </div>
</template>

<script>
  export default {
    data(){
      return {
        dataEmployer: null
      }
    },
    created(){
      this.dataEmployer = JSON.parse(localStorage.dataEmployer)
    }
  }
</script>

<style lang="scss" scoped>
  .wrapEmployer {
    width: 500px;
    max-width: 100%;
    display: flex;
    flex-flow: column;

    .btnBack {
      display: flex;
      justify-content: center;
      align-items: center;
      border-radius: 3px;
      text-decoration: none;
      background: #3E7DC0;
      color: #FFFFFF;
      width: 80px;
      height: 30px;
      margin-bottom: 10px;
    }

    .detail {
      display: flex;
      flex-flow: column;
      margin-top: 20px;
      margin-bottom: 20px;

      .items {
        display: flex;
        flex-flow: wrap;
        height: 40px;
        align-items: center;

        .key {
          width: 150px;
          font-weight: bold;
        }
      }
    }
  }
</style>