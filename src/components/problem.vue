<template>
    <div>
    	<div>props数组:{{propsArr}}</div>
    	<div>props对象:</div>
    	<div v-for="(value, key) in propsObj">
    		<span> {{ key }} : {{ value }}</span>
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
	}
}
</script>