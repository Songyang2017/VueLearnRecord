<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h2>欢迎光临红浪漫洗浴中心</h2>
    <div ref="tips">请选择一位美女为你服务</div>
    <div
      v-for="item in girls"
      :key="item"
      @click="selectGirl(item)"
      class="girl"
    >{{item}}</div>

    <h2>学生</h2>
    <div>
      <p>姓名：{{student.name}}</p>
      <p>性别：{{student.sex}}</p>
      <p>年龄：{{student.age}}</p>
    </div>

    <p>{{num}}-{{count}}</p>
    <button @click="add">增加</button>
  </div>
</template>

<script setup>
export default {
  
}
</script>
<script>
import { defineComponent, ref, reactive, toRefs, onMounted } from 'vue'
export default defineComponent({
  name: 'HelloWorld',
  props: {
    msg: String,
    count: Number
  },
  setup (props, context) {
    // const girls = ref(["大脚", "刘英", "晓红"])
    console.log(props, context)
    const tips = ref(null)
    let num = ref(0)
    const add = () => {
      console.log(props.count)
      num.value++
    }
    const data = reactive({
      student: {
        name: '小鱼',
        age: 20,
        sex: '女',
      },
      selectGirl: name => {
        alert('您选择了 ' + name + ' 服务')
      },
      girls: ref(["大脚", "刘英", "晓红"])
    })

    const data_1 = toRefs(data)
    // const selectGirl = name => {
    //   alert('您选择了 ' + name + ' 服务')
    // }

    onMounted(() => {
      tips.value.style.color = 'red'
    })
    return {
      ...data_1,
      tips,
      num,
      add
      // girls,
      // student,
      // ...student_2,
      // selectGirl
    }
  },
  methods:{
    scan(){
      // cordova.exec(function (success) {
      //   alert("success : " + success.text);
      // },
      // function (error) {
      //   alert("error : " + error);
      // }, "MideaBarcode", "scan", [1,1,1]);
    }
  }
})
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.girl {
  cursor: pointer;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
