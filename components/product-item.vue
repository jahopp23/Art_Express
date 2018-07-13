<template>
  <div>
<section class="product-display">

<div class="card">
  <div class="card-image">
    <figure class="image is-6by6" @click="isCardModalActive = true">
      <img :src="product.metadata.image.imgix_url" alt="Placeholder image">
    </figure>
  </div>
  <div class="card-content">
    <div class="media">
      <div class="media-left">
       
      </div>
      <div class="media-content">
        <p class="title is-5"><a class="title-link" @click="isCardModalActive = true"> {{ product.title }}</a></p>
        <p class="subtitle is-6">by {{product.metadata.artist }}</p>
         <button class="button is-link is-outlined is-rounded is-block" @click="addToCart(product)">
         Buy Print ${{product.metadata.price}} 
       </button>
      </div>
    </div>

    <div class="content">
 
       
  
      <br>
      <time> </time>
    </div>
  </div>
</div>


</section>
 <b-modal :active.sync="isCardModalActive" :width="640" scroll="keep">
      
            <div class="card">
                <div class="card-image">
                    <figure class="image is-4by4">
                        <img :src="product.metadata.image.imgix_url" alt="Image">
                    </figure>
                </div>
                <div class="card-content">
                    <div class="media">
                        <div class="media-left">
                            
                        </div>
                        <div class="media-content">
                            <p class="title is-4">{{ product.title }}</p>
                            <p class="subtitle is-6">Artist: {{ product.metadata.artist }} </p>
                                                        <p class="subtitle is-6">Type: {{ product.metadata.type }} </p>
                                                         <p class="subtitle is-6" v-html="product.content"></p>
                                                          <button class="button is-link is-outlined is-rounded is-block" @click="addToCart(product)">
         Buy Print ${{product.metadata.price}} 
       </button>
                        </div>
                    </div>

                    <div class="content">
                        
                        <p class="hashtags">{{ product.metadata.hashtags }}</p>
                        <br>
                        <small>11:09 PM - 1 Jan 2016</small>
                    </div>
                </div>
            </div>
          
        </b-modal>
   





  </div>
</template>




<script>

export default {
  props: ['product'],
  data() {
    return {
      isCardModalActive: false
    }
  },
  methods: {
    addToCart(item) {
      this.$store.commit('addToCart', item)
      this.$toast.open({
         message: 'Added to cart',
         type: 'is-success'
     })
    }
  }
}
</script>

<style scoped>

section .product-display{

}


.product-box {
  height: 100%;
}

.product-box button {
  margin: 0 auto;
}
.product-title {
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
  cursor: pointer;
}
.box {
  background: #f4f2f3;
  box-shadow: none;
}
.box:not(:last-child) {
    margin-bottom: auto;
}
.box .modal-box {
  background: #eee;
  
 
  
}


.box.is-bordered {
  border: 1px solid rgba(50, 115, 220, 0.2);
}
.close-button {
  position: absolute;
  right: 10px;
  font-size: 1.2rem;
  color:#000;
  top: 5px;
}
.close-button:hover {
  color: #ff3860;
}



.card{
  
 

}

.product-display .card-image img{
   max-height: 500px;
 
}

.modal-card-title{
  background-color: white;
}





.columns{
  
}


</style>
