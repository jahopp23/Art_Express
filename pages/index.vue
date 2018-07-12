<template>
  <main>
    <section class="hero is-medium" :style="{ backgroundImage: `url(${hero})` }">
      <div class="hero-body">
        <div class="container">
          <h1 class="title"> Delivering Art <em>Worldwide</em>.</h1>
          <p class= "subtitle has-text-weight-light">
            Photography | Painting | Graphic Design 
          </p>
        </div>
      </div>
    </section>

    
    <section class="section category-list">
      
        <div class="card">
       <h2>
       Types:
       </h2>

    
    <div class="type-card card-content" v-for="type in types" :key="type">
    <b-checkbox v-model="selectedTypes"
:native-value="type" class="is-warning"><p class="title is-5">{{ type }}</p></b-checkbox>
  </div>
</div>

      
         
    
          
      

      
          <div class="container">
       
              <div  v-for="product in products" :key="product._id">
                <product-item :product="product"></product-item>
              </div>
        
          </div>
     
      
    </section>
  </main>
</template>

<script>
import cosmic from '@/plugins/cosmic'
import productItem from '@/components/product-item'
export default {
  components : {
    productItem
  },
  data () {
    return {
      types: ['photography', 'painting', 'design'],
      selectedTypes: [],
      hero: this.$store.state.globals[0].metadata.hero.imgix_url
    }
  },
  computed: {
    products() {
      return this.$store.state.products.filter(el =>
        this.selectedTypes.length
        ? this.selectedTypes.includes(el.metadata.type)
        : el
      )
    }
  },

  async fetch({ store, params }) {
    await store.dispatch('getProducts')
  }
}
</script>

<style scoped>
.hero {
  background-position: center center;
  background-size: cover;
}
.box {
  background: #f4f2f3;
  box-shadow: none;
  
}

.field{
  display:inline-block;
  margin: 1.00em;
  text-align: center;
}

 .category-list .type .card {
   
}

.panel-block{
  background-color:white;
  border-color: white;
 
}

.panel-heading{
  background-color: black;
  color: white;
}

.card{
  
}

.type-card .card-content{

}



section h2{
   padding-left: 1.00rem;
   padding-top: 1.00rem;
   font-size: 1.25rem;
   font-family: 'Arial';
  
}

.section .card-content{

    display: inline-block;
    padding-bottom: 3.00rem;
 
  
}

.section{
  padding: 0;
}

.section .card-content p {
  color: white;
}

.section .card{
  width: 100%;
  text-align: center;
  position: relative;
  top: -3.00rem;
  background-color: black;
  color: white;
}



</style>
