<template>
  <div class="wrapEmployer">
    <h1>List Employer</h1>
    <TableEmployer 
      v-if="dataEmployers"
      :dataEmployers="dataEmployers"
      @sortAlphabet="sortAlphabet" />
  </div>
</template>

<script>
  import axios from 'axios'
  import TableEmployer from '~/components/TableEmployer'

  export default {
    components: {
      TableEmployer
    },
    data(){
      return {
        dataEmployers: null
      }
    },
    created(){
      this.getEmployerLists()
    },
    methods: {
      getEmployerLists() {
        axios.get('http://dummy.restapiexample.com/api/v1/employees')
        .then((response) => {
          if(response.status === 200) {
            this.dataEmployers = response.data.data
            this.dataEmployers.sort (
              function (x, y) {
                let a = x.employee_name.toUpperCase(),
                b = y.employee_name.toUpperCase();
                return a == b ? 0 : a > b ? 1 : -1;
              }
            )
          }
        })
        .catch(err => {
          console.error(err)
        })
      },
      sortAlphabet(value) {
        this.dataEmployers.sort (
          function (x, y) {
            let a = x.employee_name.toUpperCase(),
            b = y.employee_name.toUpperCase();
            if(value == 'asc') {
              return a == b ? 0 : a > b ? 1 : -1;
            } else {
              return a == b ? 0 : a < b ? 1 : -1;
            }
          }
        )
      }
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