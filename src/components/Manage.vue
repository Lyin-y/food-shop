<template>
  <div>
    <nav class="conNav">
      <ul>
        <li>
          <a href="#">管理页</a>
        </li>
      </ul>
    </nav>
    
    <div class="box">
      <div class="control">
        <div class="add">
          <dl>
            <dt>添加菜品</dt>
            <dd>
              <label for>菜名：</label>
              <input type="text" v-model="newDishes.name" />
            </dd>
            <dd>
              <label for>分类：</label>
              <input type="text" v-model="newDishes.classify" />
            </dd>
            <dd>
              <label for>单价：</label>
              <input type="text" v-model="newDishes.price" />
            </dd>
            <dd>
              <label for>图片：</label>
              <input type="text" v-model="newDishes.img" />
            </dd>
          </dl>
          <button @click="addDishes">添加</button>
        </div>
        <div class="del">
          <dl>
            <dt>删除菜品</dt>
            <dd v-for="(item,index) in this.totalDishes">
              <span>{{item.name}}</span>
              <a href="#" @click="del">删除</a>
            </dd>
            <!--<dd><span>可乐鸡翅</span><a href="#">删除</a></dd>
            <dd><span>可乐鸡翅</span><a href="#">删除</a></dd>-->
          </dl>
        </div>
      </div>
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
      newDishes: {
        //这个数据放的就是从页面里拿到的提交数据
        name: "",
        classify: "",
        price: "",
        img: "",
        num: 0 //这个字段代表菜品被点击的次数，为了在 订单页获取数据的时候取到这条属性
      },
      totalDishes: [
        { name: "可乐鸡翅", key: "-LTepXxkcvUWTbVX" },
        { name: "红烧排骨", key: "-LTepXxkcvUWTbVX" },
        { name: "糖醋里脊", key: "-LTepXxkcvUWTbVX" },
        { name: "水煮鱼", key: "-LTepXxkcvUWTbVX" }
      ]
    };
  },
  methods: {
    addDishes() {
      if (
        this.newDishes.name == "" ||
        this.newDishes.classify == "" ||
        this.newDishes.price == "" ||
        this.newDishes.img == ""
      ) {
        alert("请输入内容");
        return;
      }
      this.$axios
        .post(
          "https://wd0905222024oblsbc.wilddogio.com/dishes.json",
          this.newDishes
        )
        .then(res => {
          console.log(res);
          //根据添加的菜品的类别跳转到对应的页面
          switch (this.newDishes.classify) {
            case "热菜":
              this.$router.push("./dishes/hotDishes");
              break;
            case "凉菜":
              this.$router.push("./dishes/coldDishes");
              break;
            case "饮料":
              this.$router.push("./dishes/drink");
              break;
            case "汤":
              this.$router.push("./dishes/soup");
              break;
            case "其他":
              this.$router.push("./dishes/other");
              break;
          }

          //清空输入框
          this.newDishes.name = "";
          this.newDishes.classify = "";
          this.newDishes.price = "";
          this.newDishes.img = "";
        });
    },
    del(item) {
      //console.log(item);
      this.$axios({
        methods: "delete", //$axios的其中一种方法
        url:
          "https://wd0905222024oblsbc.wilddogio.com/dishes/" +
          item.key +
          ".json"
      })
        .then(res => {
		  console.log(res);
		  //删除后根据类型也要跳转到对应的页面
		  switch (item.classify) {
            case "热菜":
              this.$router.push("./dishes/hotDishes");
              break;
            case "凉菜":
              this.$router.push("./dishes/coldDishes");
              break;
            case "饮料":
              this.$router.push("./dishes/drink");
              break;
            case "汤":
              this.$router.push("./dishes/soup");
              break;
            case "其他":
              this.$router.push("./dishes/other");
              break;
          }
        })
        .catch(err => {
          console.log(err);
        });
    }
  },
  //跟data(),methods()同个级别
  created() {
    //这个方法在页面的实例被创建完成后触发，在这个方法里请求数据，
    this.$axios
      .get("https://wd0905222024oblsbc.wilddogio.com/dishes.json")
      .then(res => {
        //console.log(res);
        //数据请求成功后，需要子啊数据里添加一条字段（key),这是作为删除数据时候要传递的一个参数
        //添加一个key,声明一个keys,因为Object身上有一个key,res.data是把里面的key拿出来
        const keys = Object.keys(res.data);
        //console.log(keys);
        for (let v of keys) {
          //往里面赛数据
          this.totalDishes.push(res.data[v]);
        }
        //console.log(this.totalDishes);
        //把hash添加到对应的数据里
        for (let i = 0; i < this.totalDishes.length; i++) {
          //给第二条数据再添加一个字段
          this.totalDishes[i].key = key[i];
        }
      });
  }
};
/*	export default {
		data(){
			return {
				name:'kaivon'
			}
		},
		beforeRouteEnter(to, from, next){	//在路由组件内使用 
			//在当前路由被展示前调用 
			//alert('你好！');
			//alert(this.name);	//报错，beforeRouteEnter不能够访问到this对象，因为守卫触发时组件还没有被创建
			next(vm=>{
				alert(vm.name);
			});
		},
		
		beforeRouteLeave(to, from, next){	//在路由组件内使用
			//在离开当前路时调用 
			const answer=confirm('你确定要离开么？');
			if(answer){
				next();
			}else{
				next(false);	//中断当前路由的跳转
			}
		}
	}*/
</script>
<style>
dl,
dd {
  margin: 0;
  padding: 0;
}

.box {
  background: #c6c2c1;
  padding: 30px 65px 0;
  min-height: 730px;
}

/* add */
.add {
  margin-bottom: 50px;
}
.add dt,
.del dt {
  font-size: 30px;
  color: #ba6824;
}
.add dd label {
  font-size: 24px;
  color: #716154;
}
.add dd {
  margin: 10px 0;
  padding-left: 50px;
}
.add dd input {
  width: 400px;
  height: 50px;
  border: 1px solid #ccc;
  font-size: 26px;
  color: #716154;
}
.add button {
  width: 100px;
  height: 50px;
  margin-left: 250px;
}

.del {
  width: 520px;
}
.del dd {
  font-size: 30px;
  margin: 15px 0;
  padding-left: 50px;
}
.del dd a {
  float: right;
  font-size: 22px;
  color: #716154;
}
.del dd a:hover {
  text-decoration: underline;
}
</style>