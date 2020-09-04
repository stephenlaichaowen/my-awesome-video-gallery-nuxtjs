<template>
  <div>
    <PageLoader />
    <nuxt />
  </div>
</template>

<style>
:root {
  --bg-color: #2e8d86;
  --border: 1px solid;
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  background: var(--bg-color);
  font-family: 'Helvetica';
}

body {
  max-width: 1920px;
  margin: auto;
  background: var(--bg-color);
  display: flex;
  justify-content: center;
}
</style>
