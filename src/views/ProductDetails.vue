<template>

 <div id="products" class="container d-flex mb-3">
    <div v-for="products in product" :key="products.id">
      <div class="card">
        <img :src="products.img" class="card-img-top"  />
        <div class="card-body">
          <h5 class="card-title">{{ products.title }}</h5>
          <p class="card-text">{{products.categories}}</p>
          <p class="card-text">{{products.size}}</p>
          <p class="card-text">{{products.color}}</p>
          <div class="d-flex mb-3">
            <input
              type="number"
              class="form-control"
              value="1"
              min="1"
              id="addToCart${position}"
            />
          </div>
          <div>
             <button
              
              type="button"
              class="btn btn-dark ms-3"
              @click="
                (product.cart = true),
                  addtocart(JSON.parse(JSON.stringify(product)))
              "
              href="/Cart"
            >
              <i class="fas fa-cart-plus"></i>
            </button>
            <!-- <button
              v-if="product.cart"
              :disabled="product.cart"
              type="button"
              class="btn btn-dark ms-3"
              href="#"
            >
              Added
            </button> -->
              <button
                type="button"
                class="btn btn-info ms-2"
                data-bs-toggle="modal"
                data-bs-target="#editProduct"
              >
                Edit
              </button>
                <button
                type="button"
                class="btn btn-danger ms-2"
                @click="deleteProduct(products._id)"
              >
                Delete
              </button>

              <!-- Modal To Edit Product -->
            <div
              class="modal fade"
              id="editProduct"
              tabindex="-1"
              aria-labelledby="exampleModalLabel"
              aria-hidden="true"
            >
              <div class="modal-dialog">
                <div class="modal-content">
                  <div class="modal-header">
                    <h5 class="modal-title" id="exampleModalLabel">
                      Edit {{ products.title }}
                    </h5>
                    <button
                      type="button"
                      class="btn-close"
                      data-bs-dismiss="modal"
                      aria-label="Close"
                    ></button>
                  </div>
                  <div class="modal-body">
                    <div class="mb-3">
                      <label for="editTitle" class="form-label">Title</label>
                      <input
                        class="form-control"
                        type="text"
                        name="editTitle"
                        id="editTitle"
                        v-model="title"
                      />
                    </div>
                    <div class="mb-3">
                      <label for="editCategory" class="form-label"
                        >Category</label
                      >
                      <input
                        class="form-control"
                        type="text"
                        name="editCategory"
                        id="editCategory"
                        v-model="categories"
                      />
                    </div>
                    <div class="mb-3">
                      <label for="editPrice" class="form-label">Price</label>
                      <input
                        class="form-control"
                        type="text"
                        name="editPrice"
                        id="editPrice"
                        v-model="price"
                      />
                    </div>
                    <div class="mb-3">
                      <label for="editImg" class="form-label">Color</label>
                      <input
                        class="form-control"
                        type="text"
                        name="editImg"
                        id="editImg"
                        v-model="color"
                      />
                    </div>
                    <div class="mb-3">
                      <label for="editImg" class="form-label">Size</label>
                      <input
                        class="form-control"
                        type="text"
                        name="editImg"
                        id="editImg"
                        v-model="size"
                      />
                    </div>
                    <div class="mb-3">
                      <label for="editImg" class="form-label">Image URL</label>
                      <input
                        class="form-control"
                        type="text"
                        name="editImg"
                        id="editImg"
                        v-model="img"
                      />
                    </div>
                  </div>
                  <div class="modal-footer">
                    <button
                      type="button"
                      class="btn btn-secondary"
                      data-bs-dismiss="modal"
                    >
                      Close
                    </button>

                    <button
                      type="button"
                      class="btn btn-primary"
                      data-bs-dismiss="modal"
                      @click="editProduct(products._id)"
                    >
                      Save changes
                    </button>
                  </div>
                </div>
              </div>
            </div>

            <!-- Modal To Edit Product-->
          </div>
           <p class="card-text">R{{ products.price }}</p>
        </div>
        
        <div class="d-flex justify-content-center card-footer">
         
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>
export default {
  props: ["id"],
  data() {
    return {
      product: null,
      title: "",
      categories: "",
      price: "",
      desc: "",
      img: "",
      color: "",
      size: "",
    };
  },
  mounted() {
    fetch("https://ecom-store-arden.herokuapp.com/product", {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then((data) => {
        this.product = data;
        console.log(data);
      }); 
  },
   methods: {
    deleteProduct(id) {
      if (
        confirm(
          "Do you really want to delete this product!?"
        )
      ) {
        fetch("https://ecom-store-arden.herokuapp.com/product/" + id, {
          method: "DELETE",
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
          },
        })
          .then((response) => {response.json()
          alert("PRODUCT DELETED! ");
          return this.$router.push({ name: "Products" });
          })
          .catch((err) => {
            alert(err);
          });
      }
    },
  
    editProduct(id) {
      console.log(
        this.title,
        this.categories,
        this.desc,
        this.price,
        this.img,
        this.desc
      );
      fetch("https://ecom-store-arden.herokuapp.com/product/" + id, {
        method: "PUT",
        body: JSON.stringify({
          title: this.title,
          category: this.categories,
          description: this.desc,
          price: this.price,
          img: this.img,
          color: this.color,
          size: this.size,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          // Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((response) => {
          console.log(response)
          return this.$router.push({ name: "Products" });
          })
        
    },

   }

};
</script>

<style scoped>
#products {
  flex-wrap: wrap;
  gap: 20px;
}

img {
  height: 200px !important;
  object-fit: cover;
}

.card {
  width: calc((100% / 4) - 15px);
  min-width: 300px;
}

.card-title {
  text-transform: capitalize;
}
</style>
