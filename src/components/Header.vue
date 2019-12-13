<template lang="pug">
  header.header
    .header_top
      .header_top_left
        .project_logo
          img(src='../../public/assets/shapes.png', alt='shapes')
        .project_name {{ project_name }}
        .more
          .dot
          .dot
          .dot
      .header_top_right
        .avatar_wr
          img(src='../../public/assets/avatar3.jpg', alt='avatar')
          img(src='../../public/assets/avatar2.png', alt='avatar2')
          img(src='../../public/assets/avatar3.jpg', alt='avatar3')
        .btn_wr
          a.main_btn(href='#') Share
          a.second_btn(href='#')
            img(src='../../public/assets/icon.svg', alt='icon')
            |             Chat
    <header-menu></header-menu>

</template>

<script>
import HeaderMenu from './HeaderMenu.vue'

export default {
  components: {
    HeaderMenu
  },
  data () {
    return {
      project_name: 'Website Redesign'
    }
  }
}
</script>

<style lang="scss">
  @import "../../public/assets/scss/vartiables.scss";
  @import "../../public/assets/scss/mixins.scss";
  @import "../../public/assets/scss/common.scss";

  .header{
    padding: 40px 30px 14px;
    background: #fff;
    &_top{
      @include flex();
      align-items: flex-end;
      @media #{$tablets-big} {
        display: block;
      }
      &_left{
        display: flex;
        align-items: flex-end;
        @media #{$phones-big}{
          align-items: center;
        }
        .project_logo{
          width: 40px;
          height: 40px;
          background: $org;
          @include radius(6px);
        }
        .project_name{
          margin: 0 11px 0 15px;
          font-size: 32px;
          @media #{$phones-big}{
            font-size: 20px;
          }
        }
        .more{
          background: $grey;
          justify-content: center;
          width: 30px;
          height: 30px;
          @include radius(50%);
        }
      }
      &_right{
        display: flex;
        align-items: center;
        @media #{$tablets-big}{
          margin-top: 20px;
        }
        @media #{$phones-big}{
          flex-wrap: wrap;
        }
        .avatar_wr{
          img{
            width: 30px;
            height: 30px;
            @include radius(50%);
            &:nth-child(2){
              margin: 0 5px;
            }
          }
        }
        .btn_wr{
          @include flex();
          margin-left: 15px;
        }
      }
    }
    .nav{
      margin-top: 20px;
      display: flex;
      align-items: center;
      @media #{$phones-big}{
        display: block;
      }
      a{
        color: $dark;
        padding-bottom: 12px;
        opacity: .7;
        margin-left: 32px;
        &.active{
          border-bottom: 2px solid $org;
          opacity: 1;
        }
        &:first-child{
          margin-left: 0;
        }
        @media #{$phones-big}{
          margin-left: 0;
          margin-bottom: 15px;
        }
        @media #{$phones-big}{
          padding-bottom: 5px;
        }
      }
    }
  }
</style>
