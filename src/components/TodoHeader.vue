<template>
  <h1>待办清单</h1>
  <input
    type="text"
    id="ListInput"
    placeholder="请输入事项"
    @keyup.enter="addNewItem"
  />
</template>
<script>
import { nanoid } from "nanoid";
export default {
  props: ["AddTodoItem"],
  data() {
    return {};
  },
  created() {},
  computed: {},
  methods: {
    //添加新事项的方法
    addNewItem(InputList) {
      //定义一个新对象

      const todoObj = {
        id: nanoid(),
        title: InputList.target.value,
        done: false,
        isEdit: false,
      };
      //如果输入的数据为空值则弹出警告框
      if (InputList.target.value === "") {
        alert("内容不能为空");
      } else {
        this.AddTodoItem(todoObj);
        //回车添加事项完成后重置输入框内的值
        InputList.target.value = "";
      }
    },
  },
};
</script>
<style>
#ListInput {
  width: 100%;
  height: 40px;
  font-size: 1.5em;
  border: 0;
  border-bottom: 3px #fff solid;
  background-color: rgba(255, 255, 255, 0);
  box-sizing: border-box;
  padding: 1vw;
  outline: none;
  color: #fff;
}

#ListInput::placeholder {
  color: #fff;
  font-size: 0.7em;
}
</style>
