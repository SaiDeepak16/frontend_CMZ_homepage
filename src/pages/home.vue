<template>
    <Navbar></Navbar>
    <Slider></Slider>
    <Categories></Categories>
    <Products></Products>
    <Banner1
      title="Uncompromised quality for students. Get the best you deserve."
      description="We stand out by offering only the highest quality essentials, ensuring students get the best they deserve. Our commitment to excellence means you can trust every product to meet your needs reliably and durably."
    >
    </Banner1>
    <Banner></Banner>
    <Feature></Feature>
    <Banner2></Banner2>
    <Footer></Footer>
  </template>
  
  <script lang="ts" setup>
  import Slider from "../components/Slider.vue";
  import Navbar from "../components/Navbar.vue";
  import Footer from "../components/Footer.vue";
  import Feature from "../components/Feature.vue";
  import Banner from "../components/Banner1.vue";
  import Banner1 from "../components/BlackBanner.vue";
  import Categories from '../components/categories.vue';
  import Products from '../components/ProductsHome.vue'
  import Banner2 from '../components/makeitbold.vue';
  </script>
  