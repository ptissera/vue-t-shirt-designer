<template lang="pug">
  div(id="app")
    header T-Shirt
    .topnav
      router-link(to="/") Home
      router-link(to="/designer") Designer
    router-view
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
  /* Add a black background color to the top navigation */
  .topnav {
    background-color: #333;
    overflow: hidden;
  }

  /* Style the links inside the navigation bar */
  .topnav a {
    float: left;
    display: block;
    color: #f2f2f2;
    text-align: center;
    padding: 14px 16px;
    text-decoration: none;
    font-size: 17px;
    border-bottom: 3px solid transparent;
  }

  .topnav a:hover {
    border-bottom: 3px solid red;
  }

  .topnav a.active {
    border-bottom: 3px solid red;
  }
</style>
