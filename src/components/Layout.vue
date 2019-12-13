<template lang="pug">
  .container
    <Aside></Aside>
    .content
      <Header></Header>
      <router-view/>
</template>

<script>
import Aside from './Aside.vue'
import Header from './Header.vue'

export default {
  components: {
    Aside,
    Header
  }
}
</script>

<style lang="scss">
@import "../../public/assets/scss/vartiables.scss";
@import "../../public/assets/scss/mixins.scss";
@import "../../public/assets/scss/common.scss";
.content{
  width: 100%;
  height: 100%;
  margin-left: 270px;
  @media #{$tablets}{
    margin-left: 0;
  }
}
</style>
