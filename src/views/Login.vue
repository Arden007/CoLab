<template>
  <form @submit.prevent="login" class="form new-border">
    <h2 class="form-heading">Login</h2>
    <input
      class="form-input new-border-inset"
      type="username"
      v-model="username"
      placeholder="username"
    />
    <input
      class="form-input new-border-inset"
      type="password"
      v-model="password"
      placeholder="Password"
    />
    <button type="submit" class="form-btn neu-border">Sign in</button>
    <!-- <div class="form-social-login">
      <button class="form-btn neu-border form-social-btn">
        <i class="fab fa-google"></i>
      </button>
      <button class="form-btn neu-border form-social-btn">
        <i class="fab fa-facebook-f"></i>
      </button>
    </div> -->

    <p>
      Not a member?
      <router-link :to="{ name: 'SignUp' }">Create an account</router-link>
    </p>
  </form>
</template>


<script>
export default {
  data() {
    return {
      username: "",
      password: "",
    };
  },
  methods: {
    login() {
           console.log(this.username, this.password);
      fetch("https://ecom-store-arden.herokuapp.com/auth/login", {
        method: "PATCH",
        body: JSON.stringify({
          username: this.username,
          password: this.password,
        }),
        // mode: 'no-cors',
        headers: {
          "Content-type": "application/json; charset=UTF-8",
        },
      })
        .then((response) => response.json())
        .then(async(json) => {
          if(json.accessToken){
            console.log(json.accessToken)
            alert("User logged in");
             this.$router.push({ name: "Products" });
            return await localStorage.setItem("jwt", json.accessToken);
          }else
          console.log(json);
          alert("Wrong Credentials")
           this.$router.push({ name: "Home" });
        })
        .catch((err) => {
          alert(err);
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
  background: #e7e2e2;
  box-shadow: inset 8px 8px 15px #e4e4e4, inset -8px -8px 15px #ffffff;
}

.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 40px;
  gap: 20px;
  width: 100%;
  margin-inline: auto;
  max-width: 600px;
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
  color: #333;
}
</style>