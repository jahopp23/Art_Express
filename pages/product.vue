<template>
  <main>
    <section class="hero is-medium" :style="{ backgroundImage: `url(${hero})` }">
      <div class="hero-body">
        <div class="container">
          <h1 class="title"></h1>
          <p class= "subtitle has-text-weight-light">
            Photography | Painting | Graphic Design 
          </p>
        </div>
      </div>
    </section>
    <section class="section category-list">
      <div class="container">
        
        <div class="columns">
          <div class="column is-one-fifth">
            <div class="box">
              <h2 class="subtitle has-text-weight-bold has-text-black">Categories:</h2>
              <div class="field" v-for="type in types" :key="type">
                <b-checkbox v-model="selectedTypes"
                  :native-value="type" class="is-warning"> {{ type }}</b-checkbox>
              </div>
            </div>
          </div>
         
         


  
            
              
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
</style>