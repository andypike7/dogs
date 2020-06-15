<template>
  <div id="app">
    <TheHeader />
    <TheFilter />
    <div style="font-size:50px">
      <i class="mdi mdi-heart" />
      <i class="mdi mdi-heart-outline" />
    </div>
    <!-- <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div> -->
    <router-view />
  </div>
</template>

<script>
import TheHeader from '@/components/TheHeader';
import TheFilter from '@/components/TheFilter';

export default {
  components: {
    TheHeader,
    TheFilter,
  }
}
</script>
