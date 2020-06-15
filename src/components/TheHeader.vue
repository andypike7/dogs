<template>
  <header class="header">
    <a href="/" class="header__logo">
      <!-- <img class="header__logo__image" src="../assets/logo.png"> -->
      <Icon type="logo" />
    </a>

    <router-link to="/favoruites" class="header__right">
      Избранные пёсели
      <i class="mdi mdi-heart-outline header__right__heart" />
    </router-link>

    <!-- <div class="header__right" @click="toggleFavourites">
      Избранные пёсели
      <i class="mdi mdi-heart-outline header__right__heart" />
    </div> -->
  </header>
</template>

<script>
import Icon from '@/components/minor/Icon';

// toggleFavourites
export default {
  components: {
    Icon,
  },
};
</script>>

<style lang="scss">
.header {
  display: flex;
  justify-content: space-between;
  background: #151419;
  box-shadow: 0px 8px 16px rgba(0, 0, 0, 0.55);
  height: 100px;
  align-items: center;
  font-size: 16px;
}

.header__logo {
  margin-left: 60px;
}

.header__logo__image {
  width: 118px;
  height: 27px;
}

.header__right {
  display: block;
  letter-spacing: 0.01em;
  color: #626262;
  margin: 8px 58px 0 0;
  cursor: pointer;
  &:hover {
    color: yellow;
  }
}

.header__right__heart {
  font-size: 19px;
  margin-top: -4px;
  display: inline-block;
  padding-left: 4px;
}
</style>