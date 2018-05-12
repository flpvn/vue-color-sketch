<template>
  <div id="app">
    <a class="github-fork-ribbon" href="https://github.com/flpvn/vue-color-sketch" title="Fork me on GitHub">Fork me on GitHub</a>
    <div class="header-container">
      <div class="header-bg" :style="{'background-color': bgc}"></div>
      <header class="header">
        <div class="intro-wrap">
          <div class="intro" :style="{'color': bgc}">
            <h1>Vue color sketch</h1>
            <p>A Collection of Color Pickers from Sketch</p>
          </div>
        </div>
      </header>
    </div>

    <div class="demo-container">
      <div class="demo-list">
        <div class="demo-item">
          <sketch-picker v-model="colors"></sketch-picker>
          <h5>Sketch</h5>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import sketch from '../src/components/Sketch.vue'

let defaultProps = {
  hex: '#96123A',
  hsl: {
    h: 342,
    s: 0.79,
    l: 0.33,
    a: 1
  },
  hsv: {
    h: 342,
    s: 0.88,
    v: 0.59,
    a: 1
  },
  rgba: {
    r: 150,
    g: 18,
    b: 58,
    a: 1
  },
  a: 1
}

export default {
  components: {
    'sketch-picker': sketch
  },
  data () {
    return {
      colors: defaultProps
    }
  },
  computed: {
    bgc () {
      return this.colors.hex
    }
  },
  methods: {
    onOk () {
      console.log('ok')
    },
    onCancel () {
      console.log('cancel')
    },
    updateValue (value) {
      this.colors = value
    }
  },
  created () {
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
html {
  font-family: 'Source Sans Pro', 'Helvetica Neue', Arial, sans-serif;
}

.header-container {
  position: relative;
}
.header-bg {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  min-height: 153px;
  background-color: #333;
  opacity: 0.5;
  z-index: 0;
}
.header {
  display: flex;
  max-width: 780px;
  min-height: 130px;
  margin: 0 auto;
  padding: 20px 0;
}
.intro-wrap {
  flex: 1;
  margin-right: 100px;
}
.intro {
  color: rgba(0, 0, 0, 0.65098);
}
.intro > h1 {
  margin: 10px solid 0;
  font-size: 40px;
  font-weight: 700;
  line-height: 60px;
}
.intro > p {
  font-size: 16px;
  font-weight: normal;
  line-height: 22px;
}

.demo-container {
  max-width: 780px;
  min-height: 800px;
  margin: 0 auto;
  position: relative;
  z-index: 2;
}
.demo-list {
  display: flex;
  margin-bottom: 20px;
}
.demo-item {
  position: relative;
  margin-bottom: 10px;
  margin: 0 10px 0 10px;
  z-index: 2;
}
.demo-item h6 {
  margin: 0;
  padding: 5px 0;
  color: #666;
}
</style>
