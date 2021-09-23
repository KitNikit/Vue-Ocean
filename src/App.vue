<template>
  <div>
    <Header :isDark="isDark" @toggleDark="setDark" />
    <Section :isDark="isDark" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Section from './components/Section.vue';

export default {
  components: {
    Header,
    Section,
  },
  data() {
    return {
      isDark: false,
    };
  },
  methods: {
    setDark() {
      this.isDark = !this.isDark;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: 'Poppins', sans-serif;
}
</style>
