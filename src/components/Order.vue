<template>
  <div>
    <nav class="conNav">
      <ul>
        <li>
          <a href="#">订单页</a>
        </li>
      </ul>
    </nav>
    
    <div class="box">
      <table class="orderList">
        <thead>
          <tr>
            <th colspan="4">单号：122030349</th>
            <th colspan="4">
              <button>提交订单</button>
            </th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>序号</td>
            <td>菜名</td>
            <td>单价</td>
            <td>数量</td>
            <td>价格</td>
            <td>备注</td>
            <td>种类</td>
            <td>删除</td>
          </tr>
          <tr v-for="(item,index) in this.orderList">
            <td>{{index+1}}</td>
            <td>{{item.name}}</td>
            <td>{{item.price+'.00'}}</td>
            <td>
              <span></span>
              <input type="text" :value="item.num" />
              <span></span>
            </td>
            <td>{{item.price*item.num+'.00'}}</td>
            <td>加辣</td>
            <td>{{item.classify}}</td>
            <td>
              <button></button>
            </td>
          </tr>
         <!-- <tr>
            <td>1</td>
            <td>红烧排骨</td>
            <td>48.00</td>
            <td>
              <span></span>
              <input type="text" />
              <span></span>
            </td>
            <td>48.00</td>
            <td>加辣</td>
            <td>热菜</td>
            <td>
              <button></button>
            </td>
          </tr>
          <tr>
            <td>1</td>
            <td>红烧排骨</td>
            <td>48.00</td>
            <td>
              <span></span>
              <input type="text" />
              <span></span>
            </td>
            <td>48.00</td>
            <td>加辣</td>
            <td>热菜</td>
            <td>
              <button></button>
            </td>
          </tr>
          <tr>
            <td>1</td>
            <td>红烧排骨</td>
            <td>48.00</td>
            <td>
              <span></span>
              <input type="text" />
              <span></span>
            </td>
            <td>48.00</td>
            <td>加辣</td>
            <td>热菜</td>
            <td>
              <button></button>
            </td>
          </tr>
          <tr>
            <td>1</td>
            <td>红烧排骨</td>
            <td>48.00</td>
            <td>
              <span></span>
              <input type="text" />
              <span></span>
            </td>
            <td>48.00</td>
            <td>加辣</td>
            <td>热菜</td>
            <td>
              <button></button>
            </td>
          </tr>-->
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
/* {name:'可乐鸡翅',price:'22',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhm2F.jpg'},
	{name:'红烧排骨',price:'48',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhKKJ.jpg'},
	{name:'糖醋里脊',price:'30',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhnv4.jpg'},
	{name:'水煮鱼',price:'39',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhMr9.jpg'},

	*/
export default {
  data() {
    return {
      orderList: [
        { name: "可乐鸡翅", price: "22", classify: "热菜", num:1 },
        { name: "红烧排骨", price: "48", classify: "热菜", num:2 },
        { name: "糖醋里脊", price: "30", classify: "热菜", num:3 },
        { name: "水煮鱼", price: "39", classify: "热菜", num:4 }
      ]
    };
  }
};
</script>
<style>
table {
  border-collapse: collapse;
}
th,
td {
  padding: 0;
  border-bottom: 1px dashed #d3d3d3;
}
.orderList {
  width: 90%;
  margin: 0 auto;
  border-radius: 20px;
  overflow: hidden;
}
.orderList th {
  height: 100px;
  background: #7e6b5a;
  border: none;
}
.orderList th:nth-child(1) {
  text-align: left;
  font-size: 30px;
  color: #fff;
  font-weight: normal;
  padding-left: 30px;
}
.orderList th:nth-child(2) {
  text-align: right;
  padding-right: 30px;
}
.orderList th:nth-child(2) button {
  width: 174px;
  height: 60px;
  border: none;
  border-radius: 5px;
  background: #fff;
  font-size: 30px;
  color: #706456;
  cursor: pointer;
  outline: none;
  box-shadow: 0 5px 10px #42382c;
}
.orderList tbody {
  background: #fff;
}
.orderList tbody td {
  height: 90px;
  text-align: center;
  color: #716154;
  font-size: 22px;
}
.orderList tbody td:nth-of-type(odd) {
  background: #f9f9f9;
}
.orderList tbody tr:nth-child(1) td {
  height: 70px;
  color: #716154;
  font-size: 28px;
}
.orderList tbody td span {
  display: inline-block;
  width: 33px;
  height: 40px;
  vertical-align: middle;
  cursor: pointer;
  background: url(../assets/images/ico_19.gif);
}
.orderList tbody td span:nth-of-type(2) {
  background: url(../assets/images/ico_20.gif);
}
.orderList tbody td input {
  width: 96px;
  height: 41px;
  border-radius: 5px;
  border: 1px solid #d3d3d3;
  font-size: 20px;
  line-height: 41px;
  color: #ab9484;
  outline: none;
  margin: 0 15px;
  text-align: center;
}
.orderList tbody td button {
  width: 34px;
  height: 38px;
  border: none;
  outline: none;
  background: url(../assets/images/ico_21.gif);
  cursor: pointer;
}
</style>