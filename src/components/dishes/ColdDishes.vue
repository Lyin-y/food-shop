<template>
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
</template>

<script>
export default {
  data() {
    return {
      dishes: [
        {
          name: "蕨根粉",
          price: "15",
          classify: "凉菜",
          img: "https://s1.ax1x.com/2018/12/10/FGhQbR.jpg"
        },
        {
          name: "手撕鸡",
          price: "22",
          classify: "凉菜",
          img: "https://s1.ax1x.com/2018/12/10/FGh1V1.jpg"
        },
        {
          name: "蓝莓山药",
          price: "18",
          classify: "凉菜",
          img: "https://s1.ax1x.com/2018/12/10/FGhe8U.jpg"
        }
      ]
    }
  },
   //请求数据，根据菜品类型进行分类
        // created(){
        //     this.$axios.get('https://localhost:8081/dishes.json')
        //     .then(
        //         res=>{
        //             //console.log(res);
        //             //提取data 的数据
        //             const keys=Object.keys(res.data);
        //             for(let v of keys){
        //                  //过滤,要根据菜品的类型进行过滤
        //             if(res.data[v].classify=='凉菜'){
        //                  this.dishes.push(res.data[v]);
        //             }
                       
        //             }
        //         }
        //     )
        //     .catch(
        //         err=>{
        //             console.log(err);
        //         }
        //     )
        // }
};
</script>
<style>
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
				background-image: url(../../assets/images/ico_12_2.png);
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
				background: url(../../assets/images/ico_12_1.png) no-repeat center;
				background-size: 60px;
			}
			.menuName .right a:hover{
				background-image: url(../../assets/images/ico_12_2.png);
			}
</style>
