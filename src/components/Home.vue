<template>
<div>
    <div class="conNav">
        <span>Welcome To Home</span>
    </div>

    <div class="box">
        <ul class="boxList">
    <li v-for="(item, index) in this.dishes">
      <img :src="item.img" alt />
      <div class="menuName">
        <div class="left">
          <span>{{item.name}}</span>
          <p>
            RMB
            <strong>{{item.price}}/份</strong>
          </p>
        </div>
        <div class="right">
          <a href="#"></a>
        </div>
      </div>
    </li>
  </ul>
    </div>
</div> 
</template>
<script>
export default {
   data() {
       return {
           dishes:[
               {name:'可乐鸡翅',price:'22',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhm2F.jpg'},
	{name:'红烧排骨',price:'48',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhKKJ.jpg'},
	{name:'糖醋里脊',price:'30',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhnv4.jpg'},
	{name:'水煮鱼',price:'39',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhMr9.jpg'},
	{name:'蕨根粉',price:'15',classify:'凉菜',img:'https://s1.ax1x.com/2018/12/10/FGhQbR.jpg'},
	{name:'手撕鸡',price:'22',classify:'凉菜',img:'https://s1.ax1x.com/2018/12/10/FGh1V1.jpg'},
	{name:'蓝莓山药',price:'18',classify:'凉菜',img:'https://s1.ax1x.com/2018/12/10/FGhe8U.jpg'},
	{name:'可口可乐',price:'5',classify:'饮料',img:'https://s1.ax1x.com/2018/12/14/FUpzfx.jpg'},
	{name:'酸辣汤',price:'14',classify:'汤',img:'https://s1.ax1x.com/2018/12/14/FUpH6U.jpg'},
	{name:'啤酒',price:'12',classify:'其它',img:'https://s1.ax1x.com/2018/12/14/FUpTpV.jpg'}
           ]
       }
   }
}
</script>
<style>
	.conNav {
		height: 120px;
		line-height: 120px;
	}
	.conNav span{
		font-size: 45px;
		color: #fff;
		display: block;
        text-align: center;
	}
	.box{
		background: #c6c2c1;
		padding: 30px 65px 0;
		min-height: 725px;
	}
    .boxList{
				width: 900px;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
			}
			.boxList li{
				width: 420px;
				border-radius: 20px;
				background: #fff;
				overflow: hidden;
				margin-bottom: 30px;
				border: 2px solid #ccc7c3;
			}
			.boxList li:hover,.boxList li.active{
				border: 2px solid #f19903;
			}
			.boxList li:hover .menuName .right a,.boxList li.active .menuName .right a{
				background-image: url(../assets/images/ico_12_2.png);
			}
			.menuName{
				display: flex;
				justify-content: space-between;
				align-items: center;
				padding: 10px 30px;
			}
			.menuName .left{
				font-size: 26px;
				color: #796355;
			}
			.menuName .left p{
				font-size: 18px;
				color: #f39706;
			}
			.menuName .left p strong{
				font-size: 34px;
			}
			.menuName .right a{
				display: block;
				width: 60px;
				height: 60px;
				background: url(../assets/images/ico_12_1.png) no-repeat center;
				background-size: 60px;
			}
			.menuName .right a:hover{
				background-image: url(../assets/images/ico_12_2.png);
			}
</style>