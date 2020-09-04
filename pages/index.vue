<template>
  <div class="wrapper">
    <div class="container">
      <h1>My Awesome Video Gallery</h1>
      <div class="row">
        <div class="col">
          <div class="feature-img">
            <img src="/images/video_gallery/pic1.png" alt="img" width="100%" />
            <img
              src="/images/video_gallery/play.png"
              alt="img"
              class="play-btn"
              @click="toggle= !toggle"
            />
          </div>
        </div>
        <div class="col col-right">
          <div class="small-img-row" v-for="item in cards" :key="item.id">
            <div class="small-img">
              <!-- <img class="big-img" :src="item.imgSrc" alt="img" width="100%" /> -->
              <img class="big-img" :src="item.imgSrc" alt="img" />
              <img
                src="/images/video_gallery/play.png"
                alt="img"
                class="small-img play-btn"
                @click="playVideo(item.id)"
              />
            </div>
            <p>{{ item.description }}</p>

            <div class="video-player" v-if="toggle" :class="{ 'show': toggle }">
              <video width="100%" controls autoplay ref="myVideo">
                <source :src="video" type="video/mp4" />
              </video>
              <img
                src="/images/video_gallery/close.png"
                alt="close image"
                class="close-btn"
                @click="toggle = !toggle"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="overlay" v-if="toggle" :class="{ 'show': toggle }"></div>
  </div>
</template>

<script>
export default {
  layout: 'video_gallery',
  head() {
    return {
      title: 'Video Gallery'
    }
  },
  async asyncData({ $axios }) {
    const cards = await $axios.$get('/data.json')
    return { cards }
  },
  data() {
    return {
      toggle: false,
      video: '/videos/video_gallery/video.mp4',
    }
  },
  methods: {
    playVideo(id) {
      if (id === 0) this.video = '/videos/video_gallery/video.mp4'
      if (id === 1) this.video = '/videos/video_gallery/video_2.mp4'
      if (id === 2) this.video = '/videos/video_gallery/video_3.mp4'
      if (id === 3) this.video = '/videos/video_gallery/video_4.mp4'
      this.toggle = true
    }
  }
}
</script>

<style scoped>
.overlay.show {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
  display: block;
  z-index: 3;
}

.video-player.show {
  display: block;
}

.container {
  padding: 80px;
  position: relative;
  min-height: 100vh;
  height: 100%;
}

h1 {
  padding: 60px 0;
  color: #fff;
  font-size: 44px;
  text-align: center;
}

.row {
  display: flex;
  align-items: center;
  position: relative;
  flex-wrap: wrap;
}

.col {
  flex-basis: 50%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.col-right {
  display: flex;
}

.feature-img {
  width: 100%;
  margin: auto;
  position: relative;

  /* 圖片設圓角(6px 最適合)要加 overflow:hidden */
  border-radius: 6px;
  overflow: hidden;
}

.small-img-row {
  display: flex;
  background: #efefef;
  margin: 10px 0;
  align-items: center;
  border-radius: 6px;
  overflow: hidden;
  width: 85%;
}

.small-img {
  position: relative;
}

.small-img img {
  width: 100%;
}

.small-img-row p {
  padding: 0 20px;
  color: #707070;
  line-height: 22px;
  font-size: 15px;
}

.play-btn {
  width: 60px;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  cursor: pointer;
}

.small-img .play-btn {
  width: 35px;
}

.video-player {
  width: 80%;
  position: fixed;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  display: none;
  z-index: 50;
}

/* 移除 video 的 outline, 如果有的話 */
video:focus {
  outline: none;
}

.close-btn {
  position: absolute;
  top: 10px;
  right: 10px;
  width: 30px;
  cursor: pointer;
}

@media (max-width: 474px) {
  .container {
    padding: 0 1rem;
  }

  .col {
    width: 90vw;
  }

  .col-right {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(100px, 1fr));
    grid-gap: 10px;
    margin: 0;
  }

  .small-img-row {
    background: var(--bg-color);
    padding: 0;
    margin: 0;
  }

  .small-img .play-btn {
    left: 15%;
    top: 75%;
    width: 25px;
  }

  .small-img-row p {
    display: none;
  }
}

@media (max-width: 1155px) {
  .row {
    flex-direction: column;
    padding-bottom: 2rem;
  }

  .col {
    margin-top: 1rem;
  }

  .col-right {
    width: 100%;
  }

  .small-img-row {
    width: 100%;
  }
}

@media (max-width: 1450px) {
}
</style>