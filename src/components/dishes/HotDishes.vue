<template>
	<ul class="boxList">
		<li v-for="(item, index) in this.dishes">
			<img :src="item.img" alt="">
			<div class="menuName">
				<div class="left">
					<span>{{item.name}}</span>
					<p>RMB<strong>{{item.price}}/份</strong></p>
				</div>
				<div class="right">
					<a href="#" @click="order(item)"></a>
				</div>
			</div>
		</li>
	</ul>
</template>

<script>
	export default {
		data(){
			return {
				dishes:[
					{name:'可乐鸡翅',price:'22',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhm2F.jpg'},
					{name:'红烧排骨',price:'48',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhKKJ.jpg'},
					{name:'糖醋里脊',price:'30',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhnv4.jpg'},
					{name:'水煮鱼',price:'39',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhMr9.jpg'},
                
                ]
			}
        }
        
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
        //             if(res.data[v].classify=='热菜'){
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
	}
</script>
/* {name:'可乐鸡翅',price:'22',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhm2F.jpg'},
	{name:'红烧排骨',price:'48',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhKKJ.jpg'},
	{name:'糖醋里脊',price:'30',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhnv4.jpg'},
	{name:'水煮鱼',price:'39',classify:'热菜',img:'https://s1.ax1x.com/2018/12/10/FGhMr9.jpg'},
	{name:'蕨根粉',price:'15',classify:'凉菜',img:'https://s1.ax1x.com/2018/12/10/FGhQbR.jpg'},
	{name:'手撕鸡',price:'22',classify:'凉菜',img:'https://s1.ax1x.com/2018/12/10/FGh1V1.jpg'},
	{name:'蓝莓山药',price:'18',classify:'凉菜',img:'https://s1.ax1x.com/2018/12/10/FGhe8U.jpg'},
	{name:'可口可乐',price:'5',classify:'饮料',img:'https://s1.ax1x.com/2018/12/14/FUpzfx.jpg'},
	{name:'酸辣汤',price:'14',classify:'汤',img:'https://s1.ax1x.com/2018/12/14/FUpH6U.jpg'},
	{name:'啤酒',price:'12',classify:'其它',img:'https://s1.ax1x.com/2018/12/14/FUpTpV.jpg'}, */
