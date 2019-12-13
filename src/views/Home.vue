<template lang="pug">
  .inner_content
    .content_info
      .message_date Today
      .message_block
        .message_block_top
          .message_block_info
            .img
            | Darika Samak mark as done Listing on Product Hunt
            | so that we can reach as many potential users
          .time 8:40 PM
      .message_block.comment
        .message_block_top
          .message_block_info
            .img
            | Emilee Simchenko commented on Account for teams and personal in bottom style
          .time 7:32 PM
        .message_block_bottom
          | During a project build, it is necessary to evaluate the product design and development
          | against project requirements and outcomes
      .message_block.attach
        .message_block_top
          .message_block_info
            .img
            | Darika Samak uploaded 4 files on An option to search in current projects or in
            | all projects
          .time 6:02 PM
        .message_block_bottom
          .attach_wr
            span(v-for='(image, index) in images', :key='index')
              img(v-bind:src='image', @click='getIndex(index)')
    <Tasks></Tasks>

</template>

<script>
import Tasks from '../components/Tasks.vue'

export default {
  components: {
    Tasks
  },
  data () {
    return {
      images: ['../assets/nat.jpg', '../assets/nat2.jpg', '../assets/nat.jpg', '../assets/nat2.jpg']
    }
  },
  methods: {
    getIndex (index) {
      this.$root.$emit('eventing', index)
    }
  }
}
</script>

<style lang="scss">
  @import "../../public/assets/scss/vartiables.scss";
  @import "../../public/assets/scss/mixins.scss";
  @import "../../public/assets/scss/common.scss";
  .content_info{
    background: #fff;
    max-width: 720px;
    width: 100%;
    margin: 30px auto;
    @include radius(8px);
    padding: 35px 20px 35px 30px;
    @media #{$tablets-big}{
      padding: 20px;
      margin: 20px auto;
      max-width: 95%;
    }
    @media #{$phones-big}{
      max-width: 100%;
      text-align: center;
    }
    .message_date{
      font-size: 14px;
      text-transform: uppercase;
      opacity: .5;
    }
    .message_block{
      margin-top: 30px;
      &_info{
        display: flex;
        align-items: center;
        flex-basis: 75%;
        @media #{$phones-big}{
          display: block;
        }
        .img{
          background-color: #CEF9C6;
          border-radius: 50%;
          min-width: 40px;
          width: 40px;
          height: 40px;
          position: relative;
          margin-right: 20px;
          @media #{$phones-big}{
            margin: 0 auto 10px;
          }
          &::before {
            content: "";
            background: url("../../public/assets/icon2.svg") no-repeat;
            background-size: contain;
            display: block;
            width: 12px;
            height: 8px;
            left: 50%;
            top: 50%;
            transform: translate(-50%,-50%);
            position: relative;
          }
        }
      }
      &_top{
        @include flex();
        align-items: flex-start;
        @media #{$phones-big}{
          display: block;
        }
        .time{
          font-size: 14px;
          opacity: .7;
        }
      }
      &_bottom{
        margin: 20px 0 0 65px;
        @media #{$phones-big}{
          margin-left: 0;
        }
        img{
          cursor: pointer;
        }
      }
      &.comment{
        .img{
          background: $org2;
          &::before{
            background: url("../../public/assets/message.svg") no-repeat;
            background-size: contain;
            width: 12px;
            height: 11px;
          }
        }
        .message_block_bottom{
          background: $grey;
          padding: 20px 30px;
          @include radius(10px);
          font-size: 15px;
          width: 82%;
          @media #{$tablets-big} {
            width: 78%;
            padding: 10px 15px;
          }
          @media #{$phones-big}{
            width: 100%;
          }
        }
      }
      &.attach{
        .img{
          background: #E3EFFF;
          &::before{
            background: url("../../public/assets/download.svg") no-repeat;
            background-size: contain;
            width: 12px;
            height: 11px;
          }
        }
        .attach_wr{
          img{
            width: 100px;
            height: 100px;
            margin-right: 10px;
            @include radius(8px);
          }
        }
      }
    }
  }
</style>
