<template>
<!-- 1st nav -->

   <header class="p-3 bg-secondary text-white">
    <div class="container">
      <div class="home+logo"></div>
      <div class="d-flex flex-wrap align-items-center justify-content-start justify-content-lg-start">
        <a href="/" class="d-flex align-items-center mb-2 mb-lg-0 text-white text-decoration-none">
<img class="logo" style="border:1px solid; border-radius:10px; float:left;" height="50px" width="50px"    src="../assets/flyshoes.png">
        </a>

        <ul class="nav col-12 col-lg-auto me-lg-auto mb-2 justify-content-center mb-md-0">

  <li style="padding-right:10px;">
              <router-link   to="/" class="nav-link text-white">
                <svg class="bi d-block mx-auto mb-1" width="24" height="4"><use xlink:href="#home"/></svg>
                Home
              </router-link>
            </li>

            <li style="padding-right:10px;">
              <router-link    to="/products" class="nav-link text-white">
                <svg class="bi d-block mx-auto mb-1" width="24" height="4"><use /></svg>
                Products
              </router-link>
            </li>

            <li style="padding-right:10px;">
              <router-link    to="/product-details" class="nav-link text-white">
                <svg class="bi d-block mx-auto mb-1" width="24" height="4"><use /></svg>
                ProductDetails
              </router-link>
            </li>

            <li style="padding-right:10px;">
              <router-link id="mylinks"  to="/users" class="nav-link text-white">
                <svg class="bi d-block mx-auto mb-1" width="24" height="4"><use /></svg>
                Users
              </router-link>
            </li>

        

          
            
            <li text-start>
              <router-link style="padding-right:00px;font-size: 2rem; " to="/" class="nav-link text-start text-warning">
                <svg class="bi d-block mx-auto mb-1" width="24" height="4"><use xlink:href="#home"/></svg>
                 <em> FLY SHOES </em>
            </router-link>
            </li>
 <!-- <li>
                <router-link to="/about" class="nav-link text-white">
                <svg class="bi d-block mx-auto mb-1" width="24" height="4"><use xlink:href="#speedometer2"/></svg>
                About
             </router-link>
            </li>       -->
            
                <!-- <li><a href="#" class="nav-link px-2 text-white">FAQs</a></li> -->

        </ul>


        <div class="text-end">
         <div class="text-end">
             <router-link to="/add-product">  <button type="button" class="btn btn-light text-dark me-2"> Add Product </button> </router-link>
         <router-link to="/login">  <button type="button" class="btn btn-light text-dark me-2"> Login </button> </router-link>
         <router-link to="/sign-up"> <button type="button" class="btn btn-warning">Sign-up</button> </router-link>
        </div>
        </div>
      </div>
    </div>
  </header>   

 <!-- 1st nav -->
<!--  
<header>
    <div class="px-3 py-2 bg-dark text-white">
      <div class="container">
        <div class="d-flex flex-wrap align-items-center justify-content-center justify-content-lg-start">
          <a href="/" class="d-flex align-items-center my-2 my-lg-0 me-lg-auto text-white text-decoration-none">
            <svg class="bi me-2" width="40" height="32" role="img" aria-label="Bootstrap"><use xlink:href="#bootstrap"/></svg>
          </a>

          <ul class="nav col-12 col-lg-auto my-2 justify-content-center my-md-0 text-small">

            <li text-start>
              <img style="border:1px solid; border-radius:20px; " width="100" height="100px" src="@/assets/Flyshoes.png" alt="">
            </li>

            <li text-start>
              <router-link style="padding-right:00px;font-size: 2rem; " to="/" class="nav-link text-start text-primary">
                <svg class="bi d-block mx-auto mb-1" width="24" height="4"><use xlink:href="#home"/></svg>
                FLY SHOES
            </router-link>
            </li>




            <li>
              <router-link href="#" to="/" class="nav-link text-white">
                <svg class="bi d-block mx-auto mb-1" width="24" height="4"><use xlink:href="#home"/></svg>
                Home
              </router-link>
            </li>


            <li>
                <router-link to="/about" class="nav-link text-white">
                <svg class="bi d-block mx-auto mb-1" width="24" height="4"><use xlink:href="#speedometer2"/></svg>
                About
             </router-link>
            </li>

           
            <li>
               
            </li>
            
             <div class="text-end">
         <router-link to="/login">  <button type="button" class="btn btn-light text-dark me-2"> Login </button> </router-link>
         <router-link to="/sign-up"> <button type="button" class="btn btn-primary">Sign-up</button> </router-link>
        </div>
          </ul>
        </div>
      </div>
    </div>
  
  </header> -->
</template>

<script>
export default {
    
}
</script>

<style scoped>
#logo{
position:relative;
top:0;
left:0;
}

</style>