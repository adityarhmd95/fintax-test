<template>
  <div class="wrapEmployer">
    <h1>List Employer</h1>
    <FilterEmployer
      @filterTotal="filterTotal" />
    <TableEmployer 
      v-if="dataEmployers"
      :dataEmployers="dataEmployers"
      @sortAlphabet="sortAlphabet" />
    <Loader v-else />
  </div>
</template>

<script>
  import axios from 'axios'
  import FilterEmployer from '~/components/FilterEmployer'
  import TableEmployer from '~/components/TableEmployer'
  import Loader from '~/components/Loader'

  export default {
    components: {
      FilterEmployer,
      TableEmployer,
      Loader
    },
    data(){
      return {
        dataEmployersMaster: null,
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
            this.dataEmployersMaster = this.dataEmployers
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
      },
      filterTotal(value) {
        if(value == 'all') {
          this.dataEmployers = this.dataEmployersMaster
        } else {
          this.dataEmployers = this.dataEmployersMaster.slice(0, value)
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  .wrapEmployer {
    width: 500px;
    max-width: 100%;
    display: flex;
    flex-flow: column;
  }
</style>