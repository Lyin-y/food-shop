<template>
	<div id="app">
		<SideBar></SideBar>
		<div id="content">
			<div>	
				<router-view></router-view>
			</div>
		</div>
	</div>
</template>

<script>
//在一个组件使用另一个组件，需要通过import引入MenuList文件
// import MenuList from './components/MenuList';
import SideBar from './components/SlideBar'
//把组件导入进来
export default {
  components:{ //导入进来的组件要放到components里面
    // MenuList,//es6里面如果key与value相同，那就可以省略一个组件
    SideBar
  },
    mounted() {
    /**
     * 解决 css 引入图片在 github pages 无法获取的问题
     */
    const { NODE_ENV } = process.env;
    document.documentElement.className = NODE_ENV;
   }
}

</script>

<style>
@import "./assets/global.less";
body,p{
	margin: 0;
}
body{
	background: url(./assets/images/bg.jpg) center top no-repeat;
}
ul{
	margin: 0;
	padding: 0;
	list-style: none;
}
a{
	text-decoration: none;
}

#app{
	display: flex;
	width: 100%;
}
.logo{
	height: 120px;
}
#content{
	width: 100%;
	position: relative;
}
</style>

