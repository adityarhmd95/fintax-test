<template>
  <div class="container">
    <Nuxt />
  </div>
</template>

<style>
  html {
    font-family:
      'Roboto',
      'Source Sans Pro',
      -apple-system;
    font-size: 16px;
    word-spacing: 1px;
    -ms-text-size-adjust: 100%;
    -webkit-text-size-adjust: 100%;
    -moz-osx-font-smoothing: grayscale;
    -webkit-font-smoothing: antialiased;
    box-sizing: border-box;
  }

  *,
  *::before,
  *::after {
    box-sizing: border-box;
    margin: 0;
  }

  .container {
    width: 500px;
    margin: 100px auto;
    display: flex;
    flex-flow: column;
  }

</style>
