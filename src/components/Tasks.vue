<template lang="pug">
  .task_wr
    .task(v-for='(task, index) in tasks', :key='index')
      .task_number Task - {{ doMath(index) }}
      .title {{ task.title }}
      .description  {{ task.description }}
      .date Expiration date {{ task.date }}
</template>

<script>
export default {
  data () {
    return {
      tasks: [{
        title: 'Conquer the world',
        description: 'I want to conquer this world',
        date: '11.11.2020'
      }, {
        title: 'Win the lottery',
        description: 'Maybe I win',
        date: '31.12.2019'
      }, {
        title: 'Climb Mount Everest',
        description: 'Do or die',
        date: '24.06.2024'
      }]
    }
  },
  methods: {
    doMath (index) {
      return index + 1
    }
  }
}
</script>

<style lang="scss">
  @import "../../public/assets/scss/vartiables.scss";
  @import "../../public/assets/scss/mixins.scss";
  @import "../../public/assets/scss/common.scss";
  .task_wr{
    max-width: 720px;
    width: 100%;
    margin: 30px auto;
    background: #fff;
    padding: 30px;
    @include radius(8px);
    .task{
      margin-bottom: 20px;
      &_number{
        text-align: center;
        color: #000;
        font-size: 24px;
      }
      .title{
        font-size: 20px;
        color: $org;
      }
      .description{
        padding: 12px 0;
      }
      .date{
        text-align: right;
      }
    }
  }
</style>
