<template>
  <div class="view">
    <h1 class="title">{{title}}</h1>

    <input v-model="newStr" @keyup.enter="addData" type="text">

    <ul>
      <li v-for="item in items" v-bind:class="{finish:item.isFinished}" @click="toggleFinish(item)">
        {{item.text}}
      </li>
    </ul>
  </div>
</template>

<script>
    export default {
        name: "List",
      data() {
          return {
            title: "TodoList", //标题
            items: [           //待办事项
              {
                text: "今天晚上18：00跑步",
                isFinished: false
              },
              {
                text: "今天早餐",
                isFinished: true
              }
            ],
            newStr: ''
          }
      },
      methods: {
          toggleFinish(item) {
            //改变状态
            item.isFinished = !item.isFinished;
          },
          addData: function() {
            this.items.push({
              text: this.newStr,
              isFinished: false
            });
            this.newStr = '';
          }
      }
    }
</script>

<style scoped>
  .view {
    width: 400px;
    border: 1px solid gray;
    margin: 20px auto;
  }
  ul {
    padding: 0;
  }
  .view > .title {
    border-bottom: 1px solid gray;
  }
  .view > ul > li {
    margin: 10px 0;
    list-style: none;

  }
  .view  .finish {
    color: gray;
    text-decoration: line-through;
  }

</style>
