<template>
  <main>
    <section class="hero is-medium" :style="{ backgroundImage: `url(${hero})` }">
      <div class="hero-body">
        <div class="container">
          <h1 class="title">Contact Us</h1>
          <p class= "subtitle has-text-weight-light">
           </p>
        </div>
      </div>
    </section>

    
    <section class="section about-us">
      
        <div class="card">
         <div class="card-content">
             
             <h2>Please send us a message if you have any questions or are interested in selling art through ArtParty.</h2>
             <iframe width="100%" height="700" frameborder="0" src="https://6475e260-8690-11e8-bad9-277f9bdb485c.cosmicext.com/?bucket_slug=art-express&form=true"></iframe>
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

.card h2{
    font-family:Arial, Helvetica, sans-serif;
    font-weight: bolder;
}

.section .about-us .card-content{
    text-align: center;
    
}

.about-us .card{
    background-color: white;
}


</style>
