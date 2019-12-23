<template lang="pug">
  .task_wr
    .task(v-for='(task, index) in tasks', :key='index' v-if="!task.isComplete")
      .task_number Task - {{ doMath(index) }}
      .title {{ task.title }}
      .delete(@click="closeTask(index)") Done
      .description  {{ task.description }}
      .date Expiration date {{ task.date }}
    form(v-on:submit="checkForm")
      .error_div
        p(v-if='errors.length')
          b Please fix this errors:
          ul
            li(v-for='error in errors') {{ error }}
        p
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
      label Select date
      input(v-model="date")(
        type='date'
        name='date'
        format="dd/mm/yyyy"
      )
      button Add
</template>

<script>
export default {
  data () {
    return {
      title: '',
      description: '',
      date: '',
      isComplete: false,
      errors: [],
      tasks: []
    }
  },
  created () {
    this.tasks = [{
      title: 'Conquer the world',
      description: 'I want to conquer this world',
      date: '11.11.2020',
      isComplete: false
    }, {
      title: 'Win the lottery',
      description: 'Maybe I win',
      date: '31.12.2019',
      isComplete: false
    }, {
      title: 'Climb Mount Everest',
      description: 'Do or die',
      date: '24.06.2024',
      isComplete: false
    }]
  },
  methods: {
    doMath (index) {
      return index + 1
    },
    checkForm: function (e) {
      if (this.title && this.description && this.date) {
        this.tasks.push({
          title: this.title,
          description: this.description,
          date: this.date,
          isComplete: false
        })
        this.title = ''
        this.description = ''
        this.date = ''
        return true
      }

      this.errors = []

      if (!this.title) {
        this.errors.push('Please fill title.')
      }
      if (!this.description) {
        this.errors.push('Please fill description.')
      }
      if (!this.date) {
        this.errors.push('Please fill date.')
      }
      e.preventDefault()
    },
    closeTask: function (index) {
      this.tasks[index].isComplete = true
      // this.tasks.splice(index, 1)
    }
  },
  mounted () {
    let tasksLength = this.tasks.length
    this.$root.$emit('tasksLength', tasksLength)
  },
  updated () {
    let tasksLength = this.tasks.length
    this.$root.$emit('tasksLength', tasksLength)
  }
}

</script>

<style lang="scss">
  @import "../../public/assets/scss/vartiables.scss";
  @import "../../public/assets/scss/mixins.scss";
  @import "../../public/assets/scss/common.scss";
  @-webkit-keyframes font {
    from {transform: scale(1);}
    50% {transform: scale(1.1);}
    to {transform: scale(1.0);}
  }
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
        @include animation(font 2s linear);
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
  .error_div{
    p{
      color: red;
    }
  }
</style>
