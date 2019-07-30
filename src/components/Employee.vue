<template>
  <q-page class="flex flex-center">
    <div>{{employeeData}}</div>
    
    <div class="row">
    <td>
    <div class="col-sm-6">
      <p>Isi FirstName</p>
      <button class="primary" @click="getFirstNameOnly()">FirstName</button>
      <div>
        <p>{{firstNameDataOnly}}</p>
      </div>
    </div>

    <div class="col-sm-6">
      <p>Isi LastName</p>
      <button class="primary" @click="getLastNameOnly()">LastName</button>
      <div>
        <p>{{lastNameDataOnly}}</p>
      </div>
    </div>

    <div class="col-sm-6">
      <p>Submit</p>
      <button class="primary" @click="createEmployee()">Submit</button>
      <div>
        <p>{{lastNameDataOnly}}</p>
      </div>
    </div>

    <p>{{employee1}}</p>
    </td>

    </div>

  </q-page>
  
</template>

<style> 
</style>

<script>

import employee from "../api/employee/index";
export default {
  name: 'Employee',

  data(){
      return{
          employeeData: {},
          totalEmployee: 0,
          employee1 : 'AMEL',
          firstNameDataOnly: [],
          lastNameDataOnly: [],
          param: {
            "firstname": "babu",
            "lastname": "hahah",
            "email": "aku",
            "phone": "1782920"
          }
      }
  },

  methods: {
    getFirstNameOnly(){
      const self = this
      employee.getEmployee(window).then(function(datas){
        console.log('Ini data nama depan', datas)
        for(let i = 0; i<datas.length; i++){
          self.firstNameDataOnly.push(datas[i].firstname)
        }
        return datas
      }).catch(function (err){
        console.log(err)
      })
    },

    getLastNameOnly(){
      const self = this
      employee.getEmployee(window).then(function(datas){
        console.log('Ini data nama belakang', datas)
        for(let i = 0; i<datas.length; i++){
          self.lastNameDataOnly.push(datas[i].lastname)
        }
        return datas
      }).catch(function (err){
        console.log(err)
      })
    },

    createEmployee(){
      const self = this;
      employee.submitEmployee(window, self.param).then(function(res){
        return res
      }).catch(function(err){
        console.log(err)
      })
    }
  },

  beforeCreate(){
      let self = this

      employee.getEmployee(window).then(function (datas){
          return datas
      }).then(function (res){
          console.log(res)
          self.employeeData = res
      }).catch(function (err){
          console.log(err)
      })

  }
}
</script>