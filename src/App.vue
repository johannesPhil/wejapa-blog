<template>
  <div id="app">
    <div id="nav">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        version="1.1"
        width="65"
        height="65"
        style="
          shape-rendering: geometricPrecision;
          text-rendering: geometricPrecision;
          image-rendering: optimizeQuality;
          fill-rule: evenodd;
          clip-rule: evenodd;
        "
        viewBox="0 0 444 282"
        xmlns:xlink="http://www.w3.org/1999/xlink"
      >
        <g id="Layer_x0020_1">
          <metadata id="CorelCorpID_0Corel-Layer"></metadata>
          <polygon
            style="fill: #ffcc00;"
            points="0,57 102,248 103,248 107,253 108,252 155,220 69,55 "
          ></polygon>
          <path
            style="fill: #19bf69;"
            d="M223 56c2,-5 5,-10 8,-14l0 0 0 0c17,-27 38,-41 62,-42l100 0c45,0 65,31 40,83 -20,41 -52,110 -82,157 -5,7 -10,17 -15,23 -53,60 -100,-42 -114,-75l-26 51c-22,41 -60,65 -93,9 0,0 0,0 0,0 0,0 0,0 -1,0 25,0 60,-78 87,-123l-61 -125 68 0c9,19 18,37 27,56l0 0zm76 149l77 -143 -66 1c-7,0 -18,0 -24,9 -9,17 -22,41 -29,54l-1 -2 0 0c14,28 29,54 43,81z"
          ></path>
        </g>
      </svg>
      <h1>WeJapa Blog</h1>
    </div>
    <router-view />
  </div>
</template>

<style>
html,
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
* {
  box-sizing: border-box;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  display: flex;
  padding: 10px;
  background: #2c3e50;
  align-items: center;
}

#nav > * {
  margin: 0;
  margin-left: 2rem;
  color: aliceblue;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
