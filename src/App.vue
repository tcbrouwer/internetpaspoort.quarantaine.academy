<template>
  <div id="app">
    <Welcome />
    <Paspoort />
    <CourseCard :course="upstream"/>
    <router-view />
  </div>
</template>

<script lang="ts">
import Welcome from "@/views/Welcome.vue"
import Paspoort from "@/components/Paspoort.vue"
import CourseCard from "@/components/CourseCard.vue"

// content
import upstream from "@/news/upstream.json"

export default {
  name: 'App',
  components: {
    Welcome,
    Paspoort,
    CourseCard
  },
  data() {
    return {
      upstream: upstream
    }
  }
}
</script>

<style>
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif; */
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>