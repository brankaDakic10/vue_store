<template>
  <div class="container">
     <article class="col-8 bgr">
        <h4>Add new customer</h4>
            <form @submit.prevent="addNew">
           
            <div class="form-group">
                <label >First Name</label>
                <input type="text"  v-model="newCustomer.firstName" class="form-control"  placeholder=" Enter first name ">
            </div>
            <div class="form-group">
                <label >Last Name</label>
                <input type="text"  v-model="newCustomer.lastName" class="form-control"  placeholder=" Enter last name ">
            </div>
            <div class="form-group">
                <label >Email</label>
                <input type="email" v-model="newCustomer.email" class="form-control"  placeholder="Enter email ">
            </div>
            <div class="form-group">
            <button class="btn btn-success">Add new customer</button>
            </div>
            </form>
    </article>
    <article>
      <table class="table">
          <thead class="header-table"> 
                <tr>
                  <th>Id</th>
                  <th>First Name</th>
                  <th>Last Name</th>
                  <th>Email</th>
                  <th>&nbsp</th>
                  <th>&nbsp</th>
                </tr>
          </thead>
          <tbody class="body-table">
                <tr v-for="(customer, key) in customers" :key="key">
                  <td>{{customer.id}}</td>
                  <td>{{customer.firstName}}</td>
                  <td>{{customer.lastName}}</td>
                  <td>{{customer.email}}</td>
                  <td><button @click="removeCustomer(customer)" class="btn btn-secondary">Delete</button></td>
                  <td><router-link :to="'/customers/'+ customer.id" class="nav-link">Latest Purchases</router-link></td>
                </tr>
          </tbody>
      </table>
  </article>
</div>
</template>
<script>
import {customerService} from '../services/CustomerService'
export default {
  data(){
    return{
       customers:customerService.list(),
       newCustomer:{
         firstName:'',
         lastName:'',
         email:''
       }
    }
  },
  methods:{
    removeCustomer(customer){
       customerService.delete(customer)
    },
     addNew(){
      customerService.addCustomer(this.newCustomer)

    }
  }
  
}
</script>
<style scoped>
  .header-table{
     background-color: rgb(130, 189, 168)
  }
  .body-table{
     background-color: rgb(199, 228, 218)
  }
  .bgr{
    background-color: rgb(199, 228, 218)
  }

</style>

