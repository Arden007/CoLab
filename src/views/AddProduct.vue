<template>
  <!-- CODE for hiding this if not -->

  <form @submit.prevent="addProduct" class="form new-border">
    <h2 class="form-heading">Add Product</h2>

    <input
      class="form-input new-border-inset"
      type="text"
      v-model="title"
      placeholder="Title"
      required
    />

    <input
      class="form-input new-border-inset"
      type="text"
      v-model="categories"
      placeholder="Category"
      required
    />

    <input
      class="form-input new-border-inset"
      type="text"
      v-model="desc"
      placeholder="Description"
      required
    />

    <input
      class="form-input new-border-inset"
      type="text"
      v-model="img"
      placeholder="Image url"
      required
    />

    <input
      class="form-input new-border-inset"
      type="price"
      v-model="price"
      placeholder="price"
      required
    />

    <button type="submit" class="form-btn new-border"  @click="createProduct(products)">Add Product</button>
    <!-- <div class="form-social-login">
      <button class="form-btn new-border form-social-btn">
        <i class="fab fa-google"></i>
      </button>
      <button class="form-btn new-border form-social-btn">
        <i class="fab fa-facebook-f"></i>
      </button>
    </div> -->

    <!-- <p>
      Already a member?
      <router-link :to="{ name: 'Login' }">Sign in</router-link>
    </p> -->
  </form>
</template>
<script>
export default {
  // POST products HERE !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
  data() {
    return {
      title: "",
      categories: "",
      desc: "",
      img: "",
      price: "",
    };
  },
  methods: {
    createProduct() {
      console.log(this.title, this.categories, this.desc, this.img, this.price);

      if (!localStorage.getItem("jwt")) {
        alert("User not logged in");
        return this.$router.push({ name: "Login" });
      }
      fetch("https://ecom-store-arden.herokuapp.com/product", {
        method: "POST",
        body: JSON.stringify({
          title: this.title,
          categories: this.categories,
          desc: this.desc,
          price: this.price,
          img: this.img,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then((response) => console.log(response))
        .then(() => {
          alert("Product Created");
          return this.$router.push({ name: "Products" });
        });
    },
  },
};
</script>
<style>
.new-border {
  border-radius: 30px;
  background: #f5f5f5;
  box-shadow: 8px 8px 15px #e4e4e4, -8px -8px 15px #ffffff;
}
.new-border-inset {
  border-radius: 30px;
  background: #f5f5f5;
  box-shadow: inset 8px 8px 15px #e4e4e4, inset -8px -8px 15px #ffffff;
}
.form {
  display: flex;
  flex-direction: column;
  justify-content: start;
  padding: 40px;
  gap: 20px;
  width: 100%;
  max-width: 600px;
  margin-inline: auto;
}
.form-heading {
  text-align: center;
  text-transform: uppercase;
}
.form-input,
.form-btn {
  border: none;
  outline: none;
  padding: 20px;
}
.form-btn {
  cursor: pointer;
  transition: all 0.1s linear;
}
.form-btn:hover {
  transform: scale(1.05);
}
.form-social-login {
  display: flex;
  justify-content: space-between;
}
.form-social-btn {
  width: 45%;
  color: rgb(255, 190, 190);
}
</style>
