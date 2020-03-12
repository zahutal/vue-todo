<template>
  <div class="todo">
    <section class="hello flex-item">
      <h2 class="title hello-title">
        Hi
        <template v-if="userName">
          <span>{{ userName }}</span>
          <button class="correct-name" @click="correctName">You're not {{ userName }}?</button>
        </template>
      </h2>
      <div v-if="!userName">
        <p class="para">what's your name?</p>
        <input v-model.lazy="userName" />
      </div>
    </section>

    <section class="todo-list flex-item">
      <div class="list-add flex-item">
        <h2 class="title">Add to your list:</h2>
        <input placeholder="New activity" v-model="todoItem" />
        <button class="btn-add" @click="addItem(todoItem)">Add</button>
      </div>
      <div class="list-list flex-item">
        <h2 class="title">Your list:</h2>
        <ul class="list">
          <li   
            class="list-item" 
            v-for="item in todoList" 
            :key="item.id"
            @click="toggleCompleted(item)"
            :class="{ 'completed': item.completed }">
              {{item.value}}
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
      this.todoList.push({
        id: this.currentId,
        value,
        completed: false
      });
      this.currentId = this.currentId + 1;
      this.todoItem = "";
    },
    toggleCompleted: function(item) {
      item.completed = !item.completed;
    },
    correctName: function() {
      this.userName = "";
    }
  },
  data: function() {
    return {
      currentId: 1,
      userName: "",
      todoItem: "",
      todoList: []
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

.hello-title {
  font-size: 24px;
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
  min-width: 33%;
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

.correct-name {
  display: block;
  margin: 5px auto 0;
  padding: 5px 5px;
  border: none;
  color: #38495a;
  font-size: 10px;
  text-decoration: underline;
  background: none;
  cursor: pointer;
}

.completed {
  color: grey;
  text-decoration: line-through;
}

a {
  color: #42b983;
}
</style>
