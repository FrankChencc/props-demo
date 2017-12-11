<template>
	<div>
		<div>
			<!-- banner区域 -->
			<header style="width: 100%">
				<div class="nav-item el-col el-col-1">&nbsp;</div>
				<div class="nav-item el-col">Props</div>
			</header>
		</div>
		<div>
			<el-collapse v-model="activeName" accordion>
			  <el-collapse-item title="问题发现" name="1">
			    <div>父元素</div>
			    	<div>数组:{{testArr}}</div>
			    	<div>对象:</div>
			    	<div v-for="(value, key) in testObj">
			    		<span> {{ key }} : {{ value }}</span>
			    	</div>
			    	<div>
			    		<span>操作：</span>
			    		<el-button @click="changeArr()" size="small">修改数组引用</el-button>
			    		<el-button @click="pushArr()" size="small">修改数组值</el-button>
			    		<el-button @click="changeObj()" size="small">修改对象引用</el-button>
			    		<el-button @click="modifiyObj()" size="small">修改对象值</el-button>
			    	</div>
			    <div>子元素</div>
			    <problem :props-arr="testArr" :props-obj="testObj"></problem>
			  </el-collapse-item>
			  <el-collapse-item title="修改子元素" name="2">
				  <div>父元素</div>
				  	<div>数组:{{testArr}}</div>
				  	<div>对象:</div>
				  	<div v-for="(value, key) in testObj">
				  		<span> {{ key }} : {{ value }}</span>
				  	</div>
				  <div>子元素</div>
				  <child :props-arr="testArr" :props-obj="testObj"></child>
			  </el-collapse-item>
			  <el-collapse-item title="修改props" name="3">
				  <div>父元素</div>
				  	<div>数组:{{testArr}}</div>
				  	<div>对象:</div>
				  	<div v-for="(value, key) in testObj">
				  		<span> {{ key }} : {{ value }}</span>
				  	</div>
				  <div>子元素</div>
				  <props-data :props-arr="testArr" :props-obj="testObj"></props-data>
			  </el-collapse-item>
			</el-collapse>
		</div>
		<transition name="fade" mode="out-in" appear>
	    	<router-view></router-view>
	   	</transition>
   	</div>
</template>
<style scoped>
header {
	background-color: #eff2f7;
	height: 60px;
}
.nav-item {
    height: 60px;
    line-height: 60px;
	background-color: #eff2f7;
	font-size: 16px;
	font-weight: bolder;
	color: #20a0ff;
}
.nav {
	padding-right: 15px;
	padding-left: 15px;
	margin-right: auto;
	margin-left: auto;
}
a {
	text-decoration: none;
	color: #48576a !important;
}
</style>

<script>
import Problem from './problem.vue';
import Child from './child.vue';
import PropsData from './props.vue';
export default {
	components: {
		'problem': Problem,
		'child': Child,
		'props-data': PropsData
	},
	created: function () {
		let me = this;
	},
	data() {
	   return {
	     activeName: '1',
	     testArr: [1,2,3],
	     testObj: {
	        city_id: '123',
	        category: '1',
	        stime: '2016',
	        etime: '2017'
	     }
	   }
	},
	methods: {
		changeArr: function() {
			let me = this;
			me.testArr = [1,1,1,1];
		},
		pushArr: function() {
			let me = this;
			me.testArr.push(4);
		},
		changeObj: function() {
			let me = this;
			me.testObj = {
				city_id: '133',
	            category: '2',
	            stime: '2014',
	            etime: '2015'
			}
		},
		modifiyObj: function() {
			let me = this;
			me.testObj.city_id = me.testObj.city_id + '1';
		}
    }
}
</script>