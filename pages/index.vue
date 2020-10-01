<template>
  <div class="container">
    <div>
      <div v-for="image in images" :key="image.id">
        <pre>{{ image }}</pre>
        <img :src="'https://tom.imgix.net' + image.attributes.origin_path" />
      </div>

      <h1 class="title">
        nuxt-imgix-sandbox
      </h1>
      <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          rel="noopener noreferrer"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          rel="noopener noreferrer"
          class="button--grey"
        >
          GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<script>
import ImgixAPI from 'imgix-management-js';

export default {
  asyncData() {
    const imgix = new ImgixAPI({
      apiKey: ''
    });

    return imgix.request(`assets/55e4d9390d42e03905934ad4`).then(res => {
      return { images: res.data }
    });
  }
}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family:
    'Quicksand',
    'Source Sans Pro',
    -apple-system,
    BlinkMacSystemFont,
    'Segoe UI',
    Roboto,
    'Helvetica Neue',
    Arial,
    sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
