<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="less">
html, body {
  padding: 0;
  margin: 0;
  height: 100%;
}

html {
  @media screen and (min-width: 1600px) {
    font-size: 18px;
  }

  @media screen and (max-width: 1600px) {
    font-size: 16px;
  }

  @media screen and (max-width: 1200px) {
    font-size: 14px;
  }

  @media screen and (max-width: 800px) {
    font-size: 12px;
  }
}

#app {
  font-family: 'Titillium Web', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  height: 100%;
}
</style>
