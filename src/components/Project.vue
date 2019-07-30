<template>
  <div class="q-pa-md">
    <q-table
      title="Treats"
      :data="data"
      :columns="columns"
      row-key="name"
      dark
      color="amber"
    />
  </div>
</template>

<style> 
</style>

<script>
import Vue from 'vue'
import project from "../api/project/index"

export default {
  name: 'Project',

  data () {
    return {
      columns: [
        {
          name: 'id',
          required: true,
          label: 'id',
          align: 'left',
          field: row => row.id,
          sortable: true
        },
        {
          name: 'projectName',
          required: true,
          label: 'Project Name',
          align: 'left',
          field: row => row.id,
          sortable: true
        },
        {
          name: 'capacity',
          required: true,
          label: 'id',
          align: 'left',
          field: row => row.id,
          sortable: true
        },
        {
          name: 'starDate',
          required: true,
          label: 'Payment starDate',
          align: 'left',
          field: row => row.id,
          sortable: true
        },
        {
          name: 'endDate',
          required: true,
          label: 'Payment EndDate',
          align: 'left',
          field: row => row.id,
          sortable: true
        },
        {
          name: 'status',
          required: true,
          label: 'Payment Status',
          align: 'left',
          field: row => row.status,
          sortable: true
        },
        {
          name: 'createAt',
          required: true,
          label: 'Timestamp',
          align: 'left',
          field: row => row.creatAt,
          sortable: true
        }
      ],
      data: []
    }
  },

  beforeCreate(){
      let self = this

      project.getProject(window).then(function (datas){
          return datas
      }).then(function (res){
          console.log(res)
          self.data = res
      }).catch(function (err){
          console.log(err)
      })

  }
}
</script>