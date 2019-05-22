<template>
  <div class="hello">
    <div class="circle"></div>
    <h1>{{ msg }}</h1>
    <form>
      <div class="button">
        <button class="add" v-on:click="addTodo()">ADD TASK<i class="fas fa-plus-square"></i></button>
        <button class="remove" v-on:click="removeTodo()">DEL TASK<i class="fas fa-minus-square"></i></button>
      </div> 
      <div class="input-area">
        <p>入力欄: <input class="field" type="text" v-model="newTodo"></p>
        <p>TASK-NAME:{{ newTodo }}</p>
      </div>
    </form>
    <div>
      <div class="task-list">
      <transition-group>
        <div v-for="todo in todos" v-bind:key="todo.text">
          <my-component v-bind:todo="todo"></my-component>
        </div>
      </transition-group>
      </div>
    </div>
  </div>
</template>

<script>
import MyComponent from './MyComponent'

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Todo Management.',
      todos : [
        {text : 'vue-router', done: false, editing: false},
        {text : 'vuex', done: false, editing: false},
        {text : 'vue-loader', done: false, editing: false},
        {text : 'awesome-vue', done: true, editing: false},
      ],
      newTodo: ""
    }
  },
  components: {
    MyComponent
  },
  methods: {
    addTodo: function(event) {
      // 変数textにバインディングされたnewTodoをtrimされたものが入る
      // console.log(this);
      let text = this.newTodo.trim();

      if(!text){
        // textが空(false)だった場合!によって結果が反転され処理を中断(return)される
        return;
      }

      // 変数textを含んだ連想配列がpushメソッドによってtodos(配列)の一番下に追加される
      this.todos.push({
        text: text,
        done: false,
        editing: false
      });

      // 入力された文字を初期化するためにnewTodoを空文字で上書きしている
      this.newTodo = '';
    },
    removeTodo: function(event) {
      //todosの中身を(lengthはtodosの中身の個数(4-1))で繰り返し処理をする
      for(let i = this.todos.length - 1; i >= 0; i--){
        //.doneがture(チェックボックスが付いている時)に消える処理が入る
        if (this.todos[i].done) {
          // チェックボックスにチエックが入っているまとまりを１つとして削除する。第二引数が2の場合チェックがついているまとまり+1のリストが削除される
          this.todos.splice(i, 1);
        } 
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.hello{
  padding-bottom: 2rem;
}
form{
  background: #fff;
  margin: auto;
  margin-bottom: 4rem;
  border: solid 1px #ccc;
  width: 420px;
  border-radius: .3rem;
  .button{
    display: flex;
    justify-content: space-around;
    width: 22rem;
    margin: 1.5rem auto 2rem auto;
      .add{
        font-size: .8rem;
        border: solid 1px #628DFE;
        color: #628DFE;
        border-radius: .3rem;
        padding: .5rem .7rem;
        outline:none;
        cursor: pointer;
        transition: .45s;
        &:hover{
          background: #628DFE;
          color: #fff;
        }
        .fa-plus-square{
          margin-left:.5rem 
        }
      }

      .remove{
        font-size: .8rem;
        border: solid 1px #ff6767;
        color: #ff6767;
        border-radius: .3rem;
        padding: .5rem .7rem;
        outline:none;
        cursor: pointer;
        transition: .45s;
        &:hover{
          background: #ff6767;
          color: #fff;
        }
        .fa-minus-square{
          margin-left:.5rem 
        }
      }
    }

    .input-area{
      text-align: left;
      margin: auto;
      width: 18rem;
      word-break: break-all;
    }

    .field{
      width: 13rem;
      outline:none;
      border: solid 1px #ccc;
      padding: .3rem;
      border-radius: .3rem
    }
  }

    h1{
      margin: 0;
      padding: 2rem 0 2rem 0;
      position: relative;
    }

  .v-enter-active,  .v-leave-active{
    transition: 1s;
}

  .v-enter{
    opacity: 0;
    transform:translateX(1rem);
}

 .v-leave-to{
    opacity: 0;
    transform:translateX(-1rem);
}

</style>