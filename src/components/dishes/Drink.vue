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
					{name:'可口可乐',price:'5',classify:'饮料',img:'https://s1.ax1x.com/2018/12/14/FUpzfx.jpg'},
				]
			}
        },
         //请求数据，根据菜品类型进行分类
        created(){
            this.$axios.get('https://localhost:8081/dishes.json')
            .then(
                res=>{
                    //console.log(res);
                    //提取data 的数据
                    const keys=Object.keys(res.data);
                    for(let v of keys){
                         //过滤,要根据菜品的类型进行过滤
                    if(res.data[v].classify=='饮料'){
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
