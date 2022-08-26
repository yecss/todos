<template>
  <div>
    <div class="container">
      <div class="add-todo">
        <input
          class="add-enter"
          v-model="newTodo"
          @keyup.enter="addTodo"
          placeholder="请输入..."
        />
      </div>
      <ul>
        <li
          v-for="i in todo"
          :key="i.id"
          :class="i.finish ? 'line-middle' : ''"
        >
          <div class="round">
            <input type="checkbox" v-model="i.finish" :id="i.id" />
            <label :for="i.id"></label>
          </div>
          {{ i.name }}
          <div @click="deleteTodo(i.id)" class="delete-todo">删除</div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { nanoid } from "nanoid";
export default {
  name: "todo-list",
  data() {
    return {
      newTodo: "",
      todo: [
        {
          id: "001",
          name: "青花瓷",
          finish: false,
        },
        {
          id: "002",
          name: "七里香",
          finish: true,
        },
        {
          id: "003",
          name: "孤勇者",
          finish: false,
        },
        {
          id: "004",
          name: "反方向的钟",
          finish: true,
        },
        {
          id: "005",
          name: "小城夏天",
          finish: true,
        },
        {
          id: "006",
          name: "Letting Go",
          finish: false,
        },
        {
          id: "007",
          name: "红色高跟鞋",
          finish: true,
        },
      ],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo) {
        const todoObj = {
          id: nanoid(),
          name: this.newTodo,
          finish: false,
        };
        this.todo.unshift(todoObj);
        this.newTodo = "";
      } else {
        alert("请输入一个有效的名称!");
      }
    },
    deleteTodo(value) {
      const todo2 = this.todo.filter((todo) => todo.id !== value);
      this.todo = todo2;
    },
  },
};
</script>

<style scoped>
.container {
  width: 36%;
  height: 500px;
  background-color: #fff;
  border-radius: 14px;
  margin-left: auto;
  margin-right: auto;
  padding: 40px;
  overflow-y: scroll;
}
.container::-webkit-scrollbar-track {
  box-shadow: inset 0 0 6px rgba(0, 0, 0, 0.3);
  background-color: #f5f5f5;
}
.container::-webkit-scrollbar {
  width: 6px;
  background-color: #f5f5f5;
}
.container::-webkit-scrollbar-thumb {
  background-color: #bdb6b6;
}
.add-todo {
  position: relative;
  height: 46px;
  width: 100%;
  border: 2px solid #eff0f3;
  border-top: none;
  border-left: none;
  border-right: none;
}
.add-todo::before {
  content: "";
  display: inline-block;
  position: absolute;
  background-image: url(../assets/arr.svg);
  background-position: center center;
  background-size: cover;
  width: 26px;
  height: 26px;
  left: 1em;
  top: 8px;
}
.add-enter {
  border: none;
  width: 90%;
  height: 100%;
  text-indent: 1em;
  outline: none;
  margin-left: 2.2em;
  font-size: 16px;
  color: #000;
}
ul > li {
  list-style-type: none;
  line-height: 46px;
  margin-top: 20px;
  border: 2px solid #eff0f3;
  text-indent: 1em;
  color: #2a2a2a;
  border-radius: 6px;
}
li:first-child {
  margin-top: 0;
}

/* 文字中划线样式 */
.line-middle {
  text-decoration: line-through;
}
.round {
  position: relative;
  display: inline-block;
  margin-right: 0.5em;
}

li:hover .delete-todo {
  display: block;
}

.round label {
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 50%;
  cursor: pointer;
  height: 28px;
  left: 0;
  position: absolute;
  top: 9px;
  width: 28px;
}

.round label:after {
  border: 2px solid #fff;
  border-top: none;
  border-right: none;
  content: "";
  height: 6px;
  left: 7px;
  opacity: 0;
  position: absolute;
  top: 8px;
  transform: rotate(-45deg);
  width: 12px;
}

.round input[type="checkbox"] {
  visibility: hidden;
}

.round input[type="checkbox"]:checked + label {
  background-color: #ff8e3c;
}

.round input[type="checkbox"]:checked + label:after {
  opacity: 1;
}
.delete-todo {
  float: right;
  margin-right: 14px;
  cursor: pointer;
  font-size: 14px;
  display: none;
}
.delete-todo:hover {
  color: brown;
}
</style>