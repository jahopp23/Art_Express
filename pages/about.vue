<template>
  <main>
    <section class="hero is-medium" :style="{ backgroundImage: `url(${hero})` }">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">About Us</h1>
          <p class= "subtitle has-text-weight-light">
           </p>
        </div>
      </div>
    </section>

    
    <section class="section about-us">
      
        <div class="card">
         <div class="card-content">
             <p class="lead">Welcome aboard! ArtParty is a new virtual gallery space where artists of all kinds are represented (i.e. photographers, painters, graphic designers, etc.) We sell high-quality fine art and deliver internationally. Our mission is to promote the work created by hard-working creatives from all walks of life. For artists, we make life simpler by promoting their work and handling shipping. For buyers, we are a dedicated haven for emerging international art and provide museum-quality prints in large formats. You can expect to see some amazing new artwork as ArtParty sails into production!  </p>
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

.columns{
  
}

.category-list .product-item{
  display: inline-block;
  padding-bottom: 2.00em;
}


.hero-body .title{
  
 color: #eee;

 font-family: 'Raleway Dots';
 font-size: 3.00rem;
 display: block;

 


}

.hero-body{
  text-align: center;
  height: 300px;

}

.lead{
    width: 800px;
    margin: 0 auto;
   
}

.section .about-us .card-content{
    text-align: center;
}


</style>
