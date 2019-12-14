<template lang="pug">
  .task_wr
    .task(v-for='(task, index) in tasks', :key='index')
      .task_number Task - {{ doMath(index) }}
      .title {{ task.title }}
      .delete(@click="removeTask(index)") Удалить
      .description  {{ task.description }}
      .date Expiration date {{ task.date }}
    form(v-on:submit.prevent="addNewTask")
      label Task title
      input(v-model="title")(
        type='text'
        name='title'
        checked
      )
      label Task description
      input(v-model="description")(
        type='text'
        name='descr'
        checked
      )
      button Add
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
    },
    addNewTask () {
      this.tasks.push({
        title: this.title,
        description: this.description
      })
      this.title = ''
      this.description = ''
    },
    removeTask: function (index) {
      this.tasks.splice(index, 1)
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
      position: relative;
      .delete{
        position: absolute;
        top: 0;
        right: 0;
        background: #ccc;
        padding: 5px 20px;
        font-size: 12px;
        cursor: pointer;
      }
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
  form{
    border: 2px solid #ccc;
    padding: 20px;
    input{
      width: 100%;
      display: block;
      margin: 10px 0 20px;
      height: 30px;
      border: none;
      border-bottom: 1px solid #ccc;
    }
    button{
      border: none;
      background: $org;
      padding: 10px 50px;
      font-size: 16px;
    }
  }
</style>
