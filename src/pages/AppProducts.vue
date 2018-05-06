<template>
  <div class="container">
   <article class="search">
    <form class="text-center">
      <label for="searchProduct">Enter product: </label><br>
      <input v-model="searchProduct" id="searchProduct" class="text-center" type="text" placeholder="Search products"/>
      <br><br>
    </form>
  </article>
    <section>
      <table class="table">
          <thead class="header-table"> 
                <tr>
                  <th>ID</th>
                  <th>Title</th>
                  <th>Quantity</th>
                   <th>&nbsp;</th>
        
                </tr>
          </thead>
          <tbody class="body-table">
                <tr v-for="(product, key) in filterProducts" :key="key">
                  <td>{{product.id}}</td>
                  <td>{{product.title}}</td>
                  <td>{{product.quantity}}</td>
                  <td><div class="btn-group">
        <button @click="incrementQuantity(product)" class="btn btn-secondary btn-sm">+</button>
       <button @click="decrementQuantity(product)" class="btn btn-secondary btn-sm"
       v-if="product.quantity">-</button>
       </div></td>
                  
                </tr>
          </tbody>
      </table>
    </section>
  </div>
</template>
<script>
import {productService} from '../services/ProductService'

export default {
  data(){
    return{
      products:productService.list(),
      searchProduct:''
    }
  },
  computed:{
    filterProducts(){
       return this.products.filter(product =>{
           return product.title.toLowerCase().startsWith(this.searchProduct.toLowerCase())
       })
   }
  },
  methods:{
    incrementQuantity(product){
      productService.increment(product)

    },
    decrementQuantity(product){
      productService.decrement(product)
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
 .search{
    font-weight: bold;
     background-color: rgb(228, 233, 236);
 }
</style>
