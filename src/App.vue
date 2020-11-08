<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-dark bg">
      <a class="navbar-brand" href="/">
        <img src="/images/logo.jpg">
      </a>
      <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
      </button>

      <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
          <li class="nav-item active">
            <a class="nav-link active-link trainers" href="trainers.html">Trainers<span class="sr-only">(current)</span></a>
          </li>
          <li class="nav-item">
            <a class="nav-link curriculum" href="curriculum.html">Curriculum</a>
          </li>
          <li class="nav-item">
            <a class="nav-link diet" href="diet.html">Diet</a>
          </li>
          <li class="nav-item">
            <a class="nav-link service" href="service.html">Service</a>
          </li>
          <li class="nav-item">
            <a class="nav-link manage" href="manage.html">Manage</a>
          </li>
          <li class="nav-item">
            <a class="nav-link product" href="product.html">Product</a>
          </li>
        </ul>
      </div>
    </nav>

    <div>
      <router-link to="/"/>
    </div>
    <div id="menu">
      <div class ="announcement"> 
        <h4>2020-11-07 ~</h4>
        <h4>2020-11-16</h4>
      </div>
      <div class ="announcement">
        <h3>Black Friday Big Event</h3>
        <p>Most Popular Brand: Adidas, Monster</p>
      </div>
      <div id="cart">
        <router-link to="/cart">
          <div class="menu-item">
            <img src="/images/cart.png">
            <p> {{numItems}} items</p>
          </div>
        </router-link>
      </div>
    </div>
    <router-view/>

    <footer class="page-footer font-small blue-grey lighten-5">

        <div class="bottom py-4 d-flex align-items-center flex-wrap justify-content-around align-content-between" style="color:white;">
          <div class="class">
            <h6 class="text-center mb-0">Jungjin Cho</h6>
          </div>
          <div class="class">
            <h6 class="text-center mb-0">Jongwoo Lim</h6>
          </div>
          <div class="class">
            <h6 class="text-center mb-0">Jeonghaeng Heo</h6>
          </div>
          <div class="class">
            <h6 class="text-center mb-0">Kangsan Park</h6>
          </div>
          <div class="social" style="color:white;">
            <a class="git-ic mr-3" role="button" href="https://github.com/jwlim94/Creative-Project.git"><i class="fab fa-lg fa-github"></i></a>
          </div>
        </div>
        <div class="footer-copyright text-center mx-auto text-black-50 py-3">&#169; 2020 Copyright:
          <a class="dark-grey-text" href="/">Include</a>
        </div>
    </footer>

  </div>  
</template>

<script>
export default {
  name: 'App',
  data() {
    return {
    }
  },
  computed: {
    numItems() {
      return this.$root.$data.cart.length;
    }
  },
}
</script>

<style>
* {
  box-sizing: border-box;
}

.bg {
  background-color: #18224b !important;
}

#navbarNav {
  background-color: #18224b !important;
}

.nav-link {
  font-size: 1.4em;
  margin-top: 48px;
}

#menu {
  margin-top: 50px;
  border: 5px solid #18224b;
  background-color: #F4E022;
  display: flex;
  flex-direction: row;
  justify-content:space-around;
}

#cart {
  display:flex;
  justify-content: flex-end;
}

#cart img {
  width: 50px;
}

.menu-item {
  justify-self: end;
  flex-direction: column; /* 이미지와 문자열이 열(column; 위,아래)로 표현되게 함 (default: 옆으로 나란히(row)) */
}

.menu-item p {
  margin: 0px;
}

.browse {
  margin-right: 50px;
}

.fa-github {
  color: white;
}

.page-footer {
  background-color: #18224b;
  position: fixed;
  bottom: 0;
  width: 100%;
}

.footer-copyright {
  background-color: white;
}
</style>