<template>
  <div v-bind:class="{ dark: isDark }">
    <header>
      <a href="#" class="logo">Logo</a>
      <div class="righSide">
        <div
          class="btns dayNight"
          v-bind:class="{ active: isDark }"
          @click="$emit('toggleDark')"
        >
          <img src="@/assets/moon.png" />
          <img src="@/assets/sun.png" />
        </div>
        <div
          class="btns menuToggle"
          @click="menuOpen = !menuOpen"
          v-bind:class="{ active: menuOpen }"
        >
          <img src="@/assets/menu.png" />
          <img src="@/assets/close.png" />
        </div>
      </div>
    </header>
    <ul class="navigation" v-bind:class="{ active: menuOpen }">
      <li><a href="#">Home</a></li>
      <li><a href="#">About</a></li>
      <li><a href="#">Package</a></li>
      <li><a href="#">Contact</a></li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    isDark: Boolean,
  },
  data() {
    return {
      menuOpen: false,
    };
  },
};
</script>

<style lang="scss" scoped>
$black: #333;
$white: #fff;

.dark {
  .logo {
    color: $white;
  }
  .navigation {
    background: $black;
    li {
      a {
        color: $white;
      }
    }
    a:hover {
      background: $white;
      color: $black;
    }
  }
}

header {
  position: absolute;
  display: flex;
  justify-content: space-between;
  width: 100%;
  padding: 40px 100px;
  z-index: 3;

  .logo {
    position: relative;
    display: inline-flex;
    color: $black;
    text-decoration: none;
    font-size: 2em;
    font-weight: 700;
    letter-spacing: 0.05em;
    text-transform: uppercase;
  }

  img {
    width: 30px;
    height: 30px;
    &:nth-child(2) {
      display: none;
    }
  }

  .righSide {
    display: flex;
  }

  .btns {
    position: relative;
    width: 50px;
    height: 50px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    margin-left: 10px;
  }

  .active img:nth-child(2) {
    display: block;
  }

  .active img:nth-child(1) {
    display: none;
  }
}
.navigation {
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  z-index: 2;
  background: $white;
  transition: 0.5s;
  li {
    list-style: none;
    a {
      display: inline-flex;
      margin: 5px 0;
      font-size: 1.25em;
      text-decoration: none;
      color: $black;
      padding: 5px 20px;
      border-radius: 40px;
      &:hover {
        background: $black;
        color: $white;
      }
    }
  }
}
.navigation.active {
  left: 0;
}
@media (max-width: 768px) {
  header {
    padding: 20px;
  }
}
</style>
