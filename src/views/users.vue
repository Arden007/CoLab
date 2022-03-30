<template>

<!-- CODE for hiding this if not logged in -->




  <div class="users">
    <h1>Users</h1>

 <section id="gallery" style="padding-bottom: 16px ">
      <div class="container" v-for="users in user"
        :key="users._id">
        <div class="row">
          <div
            class="col-lg-4 mb-4"
          >
            <div class="card">
              <img :src="user.img" alt="" class="card-img-top" />
              <div class="card-body">
                <br />
                <h5 class="card-title">{{ users.username }}</h5>
                <p class="card-text">{{ users.email }}</p>
              </div>
              <div class="card-footer">
                <br>
                <small class="text-muted">{{ users.cart }}</small>
              </div>
              
              <br>
              <br>
              
            </div>
          </div>
         
        </div>
      </div>
    </section>


  </div>
</template>

<script>
export default {
  data() {
    return {     
      user: null,
      isAdmin: "",
      admin: "",
      username: "",
      email: "",
      cart: "",
    };
  },
  methods: {
    
    deleteUser(id) {
      if (
        confirm(
          "Do you really want to delete this user? If Yes go to ProductList view changes after json alert"
        )
      ) {
        fetch("https://ecom-store-arden.herokuapp.com/user/" + id, {
          method: "DELETE",
          headers: {
            Accept: "application/json",
            "Content-Type": "application/json",
          },
        })
          .then((response) => response.json())
          .then(() => {
            alert("USER DELETED! ");
            location.reload();
          })
          .catch((err) => {
            alert(err);
          });
      }
    },

    editUser(id) {
      fetch("https://ecom-store-arden.herokuapp.com/user/" + id, {
        method: "PUT",
        body: JSON.stringify({
          username: this.username,
          email: this.email,
          admin: this.admin,
          cart: this.cart,
        }),
        headers: {
          "Content-type": "application/json; charset=UTF-8",
          // Authorization: `Bearer ${localStorage.getItem("jwt")}`,
        },
      })
        .then((response) => response.json())
        .then((response) => console.log(response))
        .then(() => {
          alert("User Updated");
          location.reload();
        });
    },
  },

  components: {},
  created() {},
  mounted() {
    fetch("https://ecom-store-arden.herokuapp.com/product", {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then((json) => {
        this.product = json;
      });

    fetch("https://ecom-store-arden.herokuapp.com/user", {
      method: "GET",
      headers: {
        "Content-type": "application/json; charset=UTF-8",
      },
    })
      .then((response) => response.json())
      .then((json) => {
        this.user = json;
      })
      .catch((err) => {
        alert(err);
      });

    // if (this.isAdmin == false) {
    //   alert("You are Not Admin");
    //   this.$router.push({ name: "Home" });
    // }
  },
};
</script>


<style scoped>
.card {
border: 1px solid ;
  border-radius: 30px;
}

</style>