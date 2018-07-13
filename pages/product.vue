<template>
  <main>
    <section class="hero is-medium" :style="{ backgroundImage: `url(${hero})` }">
      <div class="hero-body">
        <div class="container">
          <h1 class="title"></h1>
          <p class= "subtitle has-text-weight-light">
           </p>
        </div>
      </div>
    </section>
    <div  v-for="product in products" :key="product._id">
    {{ product._id.title }}
</div>
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



.type-card .card-content{

}



section h2{
   padding-left: 1.00rem;
   padding-top: 1.00rem;
   padding-bottom: 1.00rem;
   font-size: 1.25rem;
   font-family: 'Arial';
  
}

.section .card-content{

    display: inline;
    padding-bottom: 3.00rem;
 
  
}

.section{
  padding: 0;
}

.section .card-content p {
  color: black;
}

.section .card-content span{
  color: black;
}

.section .card{
  width: 100%;
  text-align: center;
  position: relative;
 
  background-color:transparent;
  color: black;
}

.column{
  background-color: #eee;
}

.category-list .product-item{
  display: inline-block;
  padding-bottom: 2.00em;
}


.hero-body .title{
  
 color: #eee;

 font-family: 'Raleway Dots';
 font-size: 3.00rem;



 


}

.hero-body{
  text-align: center;

}

.section .card{
  
}


</style>
