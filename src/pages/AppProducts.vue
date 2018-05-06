<template>
  <div class="container">
      
    <article>
      <table class="table">
          <thead class="header-table"> 
                <tr>
                  <th>ID</th>
                  <th>Title</th>
                  <th>Quantity</th>
        
                </tr>
          </thead>
          <tbody class="body-table">
                <tr v-for="(product, key) in products" :key="key">
                  <td>{{product.id}}</td>
                  <td>{{product.title}}</td>
                  <td>{{product.quantity}}</td>
                  
                </tr>
          </tbody>
      </table>
  </article>
  </div>
</template>
<script>
import {productService} from '../services/ProductService'

export default {
  data(){
    return{
      products:productService.list()
    }
  }
}
</script>
<style scoped>
 .header-table{
   background-color: rgb(176, 182, 187);
 }

 .body-table{
   background-color: rgb(228, 233, 236);
 }
</style>
