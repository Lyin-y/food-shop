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
					<a href="#"></a>
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
					{name:'啤酒',price:'12',classify:'其它',img:'https://s1.ax1x.com/2018/12/14/FUpTpV.jpg'}
				]
			}
        },
         //请求数据，根据菜品类型进行分类
        created(){
            this.$axios.get('https://wd0905222024oblsbc.wilddogio.com/dishes.json')
            .then(
                res=>{
                    //console.log(res);
                    //提取data 的数据
                    const keys=Object.keys(res.data);
                    for(let v of keys){
                         //过滤,要根据菜品的类型进行过滤
                    if(res.data[v].classify=='其他'){
                         this.dishes.push(res.data[v]);
                    }
                       
                    }
                }
            )
            .catch(
                err=>{
                    console.log(err);
                }
            )
        }
	}
</script>
