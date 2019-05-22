<template>
  <div>
    <div v-bind:class="['task-list-item', { 'task-list-item-checked': todo.done }]">
      <input type="checkbox" v-model="todo.done">
      <input v-if="todo.editing" v-model="todo.text" v-on:keyup.enter="todo.editing = !todo.editing">
      {{todo.text}}
      <input class="edit" type="checkbox" v-model="todo.editing">
    </div>
      <img class="test3" src="../assets/tesut3.png">
  </div>
</template>

<script>
export default {
  name: 'MyComponent',
  props: {
    todo: Object
  }
}
</script>

<style scoped lang="scss">
  @mixin flex-vender() {
    display: flex;
    display: -webkit-flex;
    display: -moz-flex;
    display: -ms-flex;
    display: -o-flex;
  }

  .task-list {
    @include flex-vender;
    flex-direction: column;
    align-items: center;
    &-item {
      background: #fff;
      margin: auto;
      width: 366px;
      text-align: left;
      $element: #{&};
      color: #494949;/*文字色*/
      border-top: solid 1px #ccc;
      border-right: solid 1px #ccc;
      border-bottom: solid 1px #ccc;
      border-left: solid 25px #41b882;
      margin-bottom: -2rem;
      padding: 1rem;
      border-radius:.3rem; 
      &-checked{
        @extend #{$element};
        color: #85a6c6;
        border-color: #85a6c6;
        text-decoration-line: line-through;
      }
    }
  }

  .edit{
    position: relative;
    right: 0;
  }

  .test3{
    position: relative;
    right: -14.5rem;
    top: -1.4rem;
    height: 4rem;;
  }
</style>

