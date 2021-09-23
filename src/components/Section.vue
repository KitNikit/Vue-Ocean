<template>
  <div v-bind:class="{ dark: isDark }">
    <div class="main">
      <video muted autoplay loop src="@/assets/video.mp4"></video>
      <img class="mask" src="@/assets/mask.jpg" />
      <h2>Ocean</h2>
      <p>Vue page - 2021</p>
      <ul class="sci">
        <li>
          <a href="#"><img src="@/assets/fb.png"/></a>
        </li>
        <li>
          <a href="#"><img src="@/assets/tw.png"/></a>
        </li>
        <li>
          <a href="#"><img src="@/assets/inst.png"/></a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    isDark: Boolean,
  },
};
</script>

<style lang="scss" scoped>
$black: #333;
$white: #fff;

.dark {
  .main {
    h2 {
      color: $black;
    }
    p {
      color: $white;
    }
    .mask {
      mix-blend-mode: multiply;
      filter: invert(1);
    }
  }
}

.main {
  position: relative;
  width: 100%;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  video {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  .mask {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
    user-select: none;
    mix-blend-mode: screen;
  }
  h2 {
    position: relative;
    z-index: 1;
    font-size: 16vw;
    color: $white;
    text-shadow: 0 20px 30px rgba(0, 0, 0, 0.7);
  }
  p {
    position: absolute;
    left: 100px;
    bottom: 40px;
    font-weight: 500;
    font-size: 1.2em;
    color: $black;
  }
}

.sci {
  position: absolute;
  right: 100px;
  bottom: 40px;
  display: flex;
  flex-direction: column;
  img {
    height: 50px;
    width: 50px;
  }
  li {
    list-style: none;
  }
}

@media (max-width: 768px) {
  .main {
    p {
      left: 20px;
      bottom: 30px;
    }
  }
  .sci {
    right: 20px;
    bottom: 20px;
  }
}
</style>
