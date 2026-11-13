<template>
  <div class="hello">
    <button @click="counter += 999">点击送999 目前counter = {{ counter }}</button>
    <br>
    <br>
    <button @click="clickHandle">按钮</button>
    <br>
    <br>
    <h3>vue模板语法</h3>
    <br>
    <br>
    <br>

    <input type="text" v-model.lazy="username">
    <p>{{ username }}</p>
    <p>{{ message }}</p>
    <div>{{ rawHtml }}</div>
    <div v-html="rawHtml"></div>
    <p>{{ flag ? "林宛筠" : "柳如烟" }}</p>
    <p v-if="flag">我是叶林</p>
    <p v-else="flag">我是牧野</p>
    <p v-show=flag>你真的爱我么</p>
    <ul>
      <li v-for="item in newsList" :key="item.id">{{ item.title }}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'HelloWorld',
  data() {
    return {
      axios: {
        method: "get",
        URL: "http://localhost:8080/"
      },
      //{{}}完全是可以写在 两个标签的中间 儿v-bind 也就是: 写在标签的里面 而且 
      //父类组件往子类组件传递的时候 刚好只能写在 孩子里面
      username: "",
      //事件
      counter: 1,
      //列表渲染
      //v-for 每次新加的话 只需要渲染新加的那一块就行了
      newsList: [
        {
          id: 1001,
          title: "今日新闻1"
        },
        {
          id: 1002,
          title: "今日新闻2"
        },
        {
          id: 1003,
          title: "今日新闻3"
        }
      ],

      //变量 模板语法
      //if-else
      //-v这些都是命令的
      flag: true,
      message: "vue是天 vue是地",
      //单引号里面必须是双引号 然后双引号里面必须是单引号

      //v-show 总是会被渲染 只是经过css简单的渲染

      //v-if 惰性的 如果不符合条件 出现的机会都没有 有比较高的 切换开销
      rawHtml: '<a href="https://github.com/Zlzyq/java-backend-interview-notes">github主页链接</a>'

    }
  },
  methods: {
    clickHandle() {
      console.log("methods和data同级别 然后是方法需要调用填写括号 然后 的话类的话 不需要括号");
      //在事件中读取data中的属性 是需要通过 this.属性
      this.message = "消息被撤回了"
    }
  }
}
</script>
