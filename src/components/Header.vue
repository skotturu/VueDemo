<template>

<div>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container">
    <h1 class="navbar-brand">{{companyName}}</h1>
    <div class="collapse navbar-collapse" id="navbarResponsive">
      <ul class="navbar-nav ml-auto">
        <li class="nav-item">{{poweredBy}}</li>
        <li class="nav-item">
          <img style="overflow: hidden; width: 70px; height: 60px"
                id="pwrdbylogo" v-bind:src="companyLogo"/>
        </li>
      </ul>
    </div>
    </div>
  </nav>
</div>
</template>

<script>
export default {
  name: 'Header',
  data () {
    return {
      companyName: 'SHOP WISE',
      poweredBy:  'Powered By:',
      companyLogo: 'https://assets.awwwards.com/awards/images/2012/12/best-logo-2013-2.jpg'
      }
    }
  }
</script>
