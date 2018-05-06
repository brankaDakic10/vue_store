<template>
  <div class="container">
    <section class="card bg-light mb-3" style="max-width: 18rem;">
      <h4 class="card-header"> Customer info</h4>
      <div class="card-body">
       <h6 class="card-title">First name:  {{customer.firstName}}</h6>
       <h6 class="card-title">Last name:  {{customer.lastName}}</h6>
       <h6 class="card-title">Email:  {{customer.email}}</h6>
       
      </div>
      <div><router-link class="btn btn-link" to="/customers">Back to customers</router-link></div>
    </section>
  </div>
</template>
<script>
import { customerService } from '../services/CustomerService'
export default {
  data(){
       return{
         customer:customerService.get(this.$route.params.id)
       }
 }
}
</script>
