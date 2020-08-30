<template>
  <div class="wrapEmployer">
    <h1>List Employer</h1>
    <TableEmployer 
      v-if="dataEmployers"
      :dataEmployers="dataEmployers" />
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
          }
        })
        .catch(err => {
          console.error(err)
        })
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