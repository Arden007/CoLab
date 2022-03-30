<template>
  <div>
    <div v-if ="products">
  <h2>Products</h2>
  <div class="product-list" v-if="products">
    <router-link v-for="product of products" :key="product._id" :to="{name: 'ProductDetails', params: {id: product._id}}">
     <img class="img" :src="product.img" :alt="product.title"/>      
     {{product.title}}
    </router-link>
  </div>
</div>
<div v-else>Loading Products....</div>
  </div>
</template>

<script>
export default {
data() {
    return {
      products: null,
      title: "",
      category: "",
      description: "",
      img: "",
      price: "",

    };
  },
  //   mounted() {
  //   if (localStorage.getItem("jwt")) {
  //     fetch("https://arden-first-backend.herokuapp.com/products", {
  //       method: "GET",
  //       headers: {
  //         "Content-type": "application/json; charset=UTF-8",
  //         Authorization: `Bearer ${localStorage.getItem("jwt")}`,
  //       },
  //     })
  //       .then((response) => response.json())
  //       .then((json) => {
  //         this.products = json;
  //         this.products.forEach(async (product) => {
  //           await fetch(
  //             "https://arden-first-backend.herokuapp.com/products" + product.author,
  //             {
  //               method: "GET",
  //               headers: {
  //                 "Content-type": "application/json; charset=UTF-8",
  //                 Authorization: `Bearer ${localStorage.getItem("jwt")}`,
  //               },
  //             }
  //           )
  //             .then((response) => response.json())
  //             .then((json) => {
  //               product.author = json._id;
  //             });
  //         });
  //       })
  //       .catch(() => {
  //         alert("User not logged in");
  //       });
  //   } else {
  //     alert("User not logged in");
  //     this.$router.push({ name: "Login" });
  //   }
  // },

  mounted() {
    fetch("https://ecom-store-arden.herokuapp.com/product", {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then((data) => {
        this.products = data;
        console.log(data);
      });
    
  },
}

</script>

<style >
#products {
  flex-wrap: wrap;
}

.img{
 height: 200px !important;
object-fit: cover;
}


</style>
  



