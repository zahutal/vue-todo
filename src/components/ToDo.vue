<template>
  <div class="todo">
    <section class="hello flex-item">
      <h2 class="title">Hi {{ userName }}</h2>
      <div v-if="!userName">
        <p class="para">what's your name?</p>
        <input v-model.lazy="userName" />
      </div>
    </section>

    <section class="todo-list flex-item">
      <div class="list-add flex-item">
        <h2 class="title">Add to your list:</h2>
        <input placeholder="New item" v-model="todoItem"/>
        <button class="btn-add" @click="addItem(todoItem)">Add</button>
      </div>
      <div class="list-list flex-item">
        <h2 class="title">Your list:</h2>
        <ul class="list">
          <li class="list-item" v-for="item in todoList" :key="item">
            {{item}}
          </li>
        </ul>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  props: {
    msg: String
  },
  methods: {
    addItem: function(value) {
      console.log("pingu", this);
      console.log(this.todoList);
      this.todoList.push(value);
    }
  },
  data: function() {
    return {
      userName: false,
      todoItem: "",
      todoList: ['zrobic paczingsun', 'uakame']
    };
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.todo {
  display: flex;
  flex-direction: column;
}
.title {
  font-size: 18px;
  font-weight: bold;
}
.todo-list {
  margin-top: 40px;
  padding: 40px;
  background-color: #f5f5f5;
  border-radius: 6px;
  display: flex;
  flex-direction: row;
}
.list-list,
.list-add {
  text-align: left;
}
.list-add {
  flex-grow: 1;
}
.list-list {
  flex-grow: 2;
}
.list {
  padding: 0;
}
.list-item {
  display: block;
  padding-bottom: 10px;
}
a {
  color: #42b983;
}
</style>
