<template lang="pug">
  aside.aside
    .aside_top
      a.logo(href='/')
        img(src='../../public/assets/logo.svg', alt='logo')
        span {{ heading }}
      .search
    .aside_user
      .aside_user_left
        img(src='../../public/assets/avatar2.png', alt='avatar')
        .info
          p {{ name }}
          span {{ position }}
      .aside_user_right.more
        .dot
        .dot
        .dot
    .aside_bottom
      .task
        #completed.task_block(@click='confirm')
          p#completed_num {{ completed.count }}
          span {{ completed.text }}
        #open.task_block
          p#open_num {{ open.count }}
          span {{ open.text }}
      .menu
        p Menu
        <aside-menu></aside-menu>
</template>

<script>
import AsideMenu from './AsideMenu.vue'

export default {
  name: 'app',
  components: {
    AsideMenu
  },
  data () {
    return {
      heading: 'Projectus',
      name: 'Jean Gonzales',
      position: 'Product Owner',
      completed: {
        count: 372,
        text: 'Completed Tasks'
      },
      open: {
        count: 11,
        text: 'Open Tasks'
      }
    }
  },
  methods: {
    confirm () {
      // eslint-disable-next-line no-restricted-globals
      const sure = confirm('Are you sure you want to change the number of tasks?')
      if (sure === true) {
        if (this.open.count > 0) {
          // eslint-disable-next-line no-plusplus
          this.open.count--
          // eslint-disable-next-line no-plusplus
          this.completed.count++
        } else {
          alert('Yay Open tasks completed')
        }
      }
    }
  }
}
</script>

<style lang="scss">
  @import "../../public/assets/scss/vartiables.scss";
  @import "../../public/assets/scss/mixins.scss";
  @import "../../public/assets/scss/common.scss";
  .aside{
    background: $black;
    max-width: 270px;
    width: 100%;
    height: 100%;
    position: fixed;
    top: 0;
    left: 0;
    @media #{$tablets}{
      position: static;
      max-width: 100%;
    }
    &_top{
      @include flex();
      padding: 30px 25px 30px 30px;
      a{
        color: #fff;
        @include flex();
        text-transform: uppercase;
        img{
          margin-right: 13px;
        }
      }
      .search{
        position: relative;
        width: 16px;
        height: 16px;
        cursor: pointer;
        &::before{
          content: "";
          position: absolute;
          top: 0;
          left: 0;
          width: 16px;
          height: 16px;
          background: url("../../public/assets/searh.svg") no-repeat;
        }
      }
    }
    &_user{
      background: #202020;
      padding: 16px 20px 16px 30px;
      @include flex();
      color: #fff;
      &_left{
        display: flex;
        align-items: center;
        justify-content: flex-start;
        img{
          width: 48px;
          height: 48px;
          @include radius(50%);
        }
        .info{
          margin-left: 13px;
          p{
            font-size: 14px;
            line-height: 17px;
          }
          span{
            font-size: 12px;
            color: #9B9B9B;
          }
        }
      }
    }
    &_bottom{
      padding: 20px 30px;
      #completed{
        cursor: pointer;
      }
      .task{
        display: flex;
        align-items: center;
        justify-content: flex-start;
        color: #fff;
        &_block{
          &:first-child{
            margin-right: 19px;
          }
          p{
            font-size: 20px;
            line-height: 24px;
          }
          span{
            font-size: 12px;
            line-height: 14px;
            opacity: .5;
          }
        }
      }
      .menu{
        margin-top: 31px;
        p{
          color: #878787;
          font-size: 12px;
          text-transform: uppercase;
        }
        ul{
          li{
            padding-top: 18px;
          }
          a{
            color: #fff;
            font-size: 14px;
            @include transition(color .2s linear);
            &:hover{
              color: $org;
            }
            &.count{
              display: flex;
              align-items: center;
              span{
                background: $org;
                width: 20px;
                height: 20px;
                @include radius(50%);
                display: inline-block;
                vertical-align: middle;
                text-align: center;
                color: $dark;
                margin-left: 8px;
                line-height: 20px;
              }
            }
          }
        }
      }
    }
  }
</style>
