<template>
  <div class="landing">
<!-- hero message -->

<div class="px-4 pt- my- text-center border-bottom">
    <h1 class="display-3 fw-bold">Step Fly</h1>
       <em> <h3 class="display-4 text-warning fw-bold">Kick it with us</h3></em>
<br>
    <!-- <div class="col-lg-6 mx-auto">
      <p class="lead mb-4">Shop with us and take fly steps towards your destiny.</p>
      <div class="d-grid gap-2 d-sm-flex justify-content-sm-center mb-5">
        <button style="border:1px solid; border-radius:40px;" type="button" class="btn btn-primary btn-lg px-4 me-sm-3">Log in</button>
        <button   style="border:1px solid; border-radius:40px;" type="button" class="btn btn-outline-warning btn-lg px-4">Sign-up</button>
      </div>
    </div> -->
   
  </div>

<br><br>

<!-- hero message -->


<!-- promo carousels -->


<div id="demo" class="carousel slide" data-ride="carousel">
  <ul class="carousel-indicators">
    <li data-target="#demo" data-slide-to="0" class="active"></li>
    <li data-target="#demo" data-slide-to="1"></li>
    <li data-target="#demo" data-slide-to="2"></li>
  </ul>
  <div class="carousel-inner">
    <div class="carousel-item active">
      <img src="" alt="Los Angeles" width="300" height="100">
      <div class="carousel-caption">
        <h3></h3>
      </div>
    <p class="text-success ">A Ma Maniere x Nike Air Jordan 3</p>
<br>
    </div>
    <div class="carousel-item">
      <img src="" alt="Chicago" width="300" height="100">
      <div class="carousel-caption">
        <h3></h3>
      </div> 
   <p class="text-success "  >COMME des GARÇONS x Nike Air Foamposite</p>

      <br>  
    </div>
    <div class="carousel-item">
      <img src="" alt="New York" width="300" height="100">
      <div class="carousel-caption">
        <h3></h3>
      </div> 
               <p class="text-success "  >Patta x Nike Air Max 1</p>
      <br> 
    </div>
  </div>
  <a class="carousel-control-prev" href="#demo" data-slide="prev">
    <span class="carousel-control-prev-icon"></span>
  </a>
  <a class="carousel-control-next" href="#demo" data-slide="next">
    <span class="carousel-control-next-icon"></span>
  </a>
</div>

<br><br>


 <!-- end of promo carousels -->


  
  
  </div>
<!--landi promo -->

  
</template>

<script>


export default {
  name: "Landing",
  props: {
    msg: String,
  },
};


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


/* carousels styling */
  /* Make the image fully responsive */
  .carousel-inner img {
    object-fit:cover;
    border-radius:20px;
    width: 500px;
    height: 300px;
  }



h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
