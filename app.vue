<template>
    <div id="app">
      <nav>
        <router-link to="/">Home</router-link>
        <router-link to="/about">About</router-link>
      </nav>
  
      <router-view></router-view>
  
      <footer>
        © 2024 My Awesome App
      </footer>
    </div>
  </template>
  
  <script>
  export default {
    name: 'App',
  }
  </script>
  
  <style>
  body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 0;
  }
  
  #app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  
  nav {
    background-color: #333;
    padding: 1rem;
  }
  
  nav a {
    color: #fff;
    text-decoration: none;
    margin-right: 1rem;
  }
  
  footer {
    background-color: #333;
    color: #fff;
    padding: 1rem;
    margin-top: auto;
    text-align: center;
  }
  </style>
  