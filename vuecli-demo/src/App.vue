<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model.trim="name" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model.trim="age" />
    </div>
    <div>
      <span>性别:</span>
      <select v-model="sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="add">添加/修改</button>
    </div>
    <div>
      <table border="1" cellpadding="10" cellspacing="0">
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="item in arr" :key="item.id">
          <td>{{ item.id }}</td>
          <td>{{ item.name }}</td>
          <td>{{ item.age }}</td>
          <td>{{ item.sex }}</td>
          <td>
            <button @click="del(item.id)">删除</button>
            <button @click="edit(item.id)">编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>
<script>
export default {
  name: "App",
  data() {
    return {
      arr: [
        {
          id: "1",
          name: "one",
          age: 18,
          sex: "男",
        },
        {
          id: "2",
          name: "two",
          age: 20,
          sex: "女",
        },
      ],
      name: "",
      age: "",
      sex: "",
    };
  },
  methods: {
    add(){
      if(this.name==''||this.age==""||this.sex=='') return alert('请您完善信息')
      const id=this.list[this.arr.length-1]?this.arr[this.arr.length-1].id+1:100
      this.arr.push({
        id,
        name:this.name,
        age:this.age,
        sex:this.sex,
        })
    this.name=''
    this.price=0
    },
    del(id) {
      const index = this.arr.findIndex((ele) => ele.id == id);
      this.arr.splice(index, 1);
    },
    edit(){

    }
  },
};
</script>
<style></style>
