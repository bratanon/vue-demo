<template>
    <div id="app">
        <h1>Todo List</h1>
        <div class="container">

            <section class="form">
                <div>
                    <input v-model="inputField" v-on:keyup.enter="addTodo" placeholder="Todo Item" />
                    <button v-on:click="addTodo" class="btn btn-primary">Add Todo</button>
                </div>
            </section>

            <section class="container">
                <div>
                    <ul class="list-group">
                        <li v-for="todo in todoList" class="list-item">
                            <span>{{ todo.name }}</span>
                            <button @click="deleteTodo(todo)" class="delete">Delete</button>
                        </li>
                    </ul>
                </div>
            </section>

        </div>

    </div>
</template>

<script>

  export default {
    name: 'app',
    data () {
      return {
        inputField: '',
        todoList: []
      }
    },
    methods: {
      addTodo: function() {
        const todo = this.inputField;
        this.todoList.push({name: todo, complete: false});
        this.inputField = '';
      },

      deleteTodo: function(todo) {
        const index = this.todoList.indexOf(todo);
        this.todoList.splice(index, 1);
      },
    }
  }
</script>

<style>
    #app {
        font-family: Helvetica, Arial, sans-serif;
        color: #2c3e50;
        margin: 100px;
    }

    .form input,
    .form button {
        font-size: 20px;
        border-radius: 4px;
        border: 1px solid #666;
        padding: .6rem;
    }

    ul {
        list-style-type: none;
        padding: 0;
    }
    li {
        display: inline-block;
        margin: 0;
    }

    .list-item {
        width: 900px;
        display: flex;
        padding: .6rem;
        border-radius: 4px;
        border: 1px solid #666;
        margin-top: 2rem;
    }

    .list-item span {
        flex-grow: 1;
        align-content: center;
    }

    .list-item button {
        flex-grow: 0;
    }


    .delete {
        color: #fff;
        background-color: #ff4f59;
        cursor: pointer;
        border-radius: 4px;
        border: 1px solid #ff0000;
        padding: .6rem;
        font-size: 16px;
    }


</style>
