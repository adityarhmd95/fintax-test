<template>
  <div class="container">
    <Nuxt />
  </div>
</template>

<style lang="scss">
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

    @media screen and (max-width: 700px) {
      padding: 0 15px;
      margin: 30px auto;
    }
  }

  .hint {
    font-size: 11px;
    font-style: italic;
  }

</style>
