<template>
  <div id="app">
    <div class="container">
      <div class="form-group">
        <div class="input-group">
          <h4>品牌管理</h4>
        </div>
      </div>
      <table class="table table-bordered table-hover mt-2">
        <thead>
          <tr>
            <th>编号</th>
            <th>资产名称</th>
            <th>价格</th>
            <th>创建时间</th>
            <th>操作</th>
          </tr>
          <tr v-if="list.length==0" style="text-align:center">
        <td colspan="4" >没有数据咯~</td>
      </tr>
        </thead>
        <tbody>
          <tr v-for="item in list" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td :class="{red:item.price>100}">{{item.price}}</td>
            <td>{{item.time}}</td>
            <td><a href="#" @click="del(item.id)">删除</a></td>
          </tr>
        </tbody>
      </table>
      <form class="form-inline" style="display:flex;">
        <div class="form-group">
          <div class="input-group">
            <input
              type="text"
              class="form-control"
              placeholder="资产名称"
              v-model.trim="name"
            />
          </div>
        </div>
        &nbsp;&nbsp;&nbsp;&nbsp;
        <div class="form-group">
          <div class="input-group">
            <input
              type="text"
              class="form-control"
              placeholder="价格"
              v-model.number="price"
            />
          </div>
        </div>
        &nbsp;&nbsp;&nbsp;&nbsp;
        <button class="btn btn-primary" @click.prevent="add">添加资产</button>
      </form>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data () {
    return {
      list: [
        { id: 100, name: "外套", price: 199, time: new Date('2010-08-12')},
        { id: 101, name: "裤子", price: 34, time: new Date('2013-09-01') },
        { id: 102, name: "鞋", price: 25.4, time: new Date('2018-11-22') },
        { id: 103, name: "头发", price: 19900, time: new Date('2020-12-12') }
      ],
      name:'',
      price:0
    }
  },
  methods: {
    add(){
      if(this.name==''||this.price==0||this.price=='') return alert('请您完善信息')
      const id=this.list[this.list.length-1]?this.list[this.list.length-1].id+1:100
      this.list.push({
        id,
        name:this.name,
        price:this.price,
        time:new Date()
    })
    this.name=''
    this.price=0
    },
    del(id){
      const index=this.list.findIndex(ele=>ele.id==id)
      this.list.splice(index,1)
    }
  }
}
</script>

<style>
  .red{
  color: red;
}
</style>
