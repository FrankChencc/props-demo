<template>
    <div>
    	<div>props数组:{{propsArr}}</div>
    	<div>props对象:</div>
    	<div v-for="(value, key) in propsObj">
    		<span> {{ key }} : {{ value }}</span>
    	</div>
    	<div>
    		<span>操作：</span>
    		<el-button @click="changeArr()" size="small">修改数组引用</el-button>
    		<el-button @click="pushArr()" size="small">修改数组值</el-button>
    		<el-button @click="changeObj()" size="small">修改对象引用</el-button>
    		<el-button @click="modifiyObj()" size="small">修改对象值</el-button>
    	</div>
	    <div>子元素数组:{{childArr}}</div>
	    <div>子元素对象:</div>
	    <div v-for="(value, key) in childObj">
	    	<span> {{ key }} : {{ value }}</span>
	    </div>
    </div>
</template>

<style scoped>
.demo-block {
    border: 1px solid #eaeefb;
    border-radius: 4px;
    transition: .2s;
}
.source, .content, .page {
  padding: 24px;
}
.operate {
	margin: 20px;
}
</style>

<script>
export default {
	props: ['propsArr','propsObj'],
	data() {
		return {
		  childArr: this.propsArr,
		  childObj: this.propsObj
		}
	},
	methods: {
		changeArr: function() {
			let me = this;
			me.propsArr = [1,1,1,1];
		},
		pushArr: function() {
			let me = this;
			me.propsArr.push(4);
		},
		changeObj: function() {
			let me = this;
			me.propsObj = {
				city_id: '133',
	            category: '2',
	            stime: '2014',
	            etime: '2015'
			}
		},
		modifiyObj: function() {
			let me = this;
			me.propsObj.city_id = me.propsObj.city_id + '1';
		}
	}
}
</script>