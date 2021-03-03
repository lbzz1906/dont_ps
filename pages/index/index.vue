<template>
	<view><text>\n</text>
		<view style="display: flex;justify-content: center;border-bottom: #858B9C 1px solid;padding-bottom: 20px;">
			<radio value="in" :checked="stua" @click='dataClick' />进校</radio>
			<radio value="out" :checked="!stua" @click='dataClick' style="margin-left: 40px;">出校</radio>
		</view>
		<view style="display: flex;justify-content: center;margin-top: 20px;">
			<view style="float: left;margin-left: 20px;">
			<text style="margin-top: 10px;display: block;">姓名:\n</text>
			<text style="margin-top: 13px;display: block;">学号:\n</text>
			<text style="margin-top: 14px;display: block;">专业:\n</text>
		</view>
		<view style="float: left;margin-left: 20px;">
			<input type='text' v-model="name" />
			<input type="number" v-model="number" />
			<input type='text' v-model="major" style="margin-bottom: 20px;" />
		</view>
		</view>
		

		<text>\n</text>
		<button style="background-color: #9085ff;width: 100%;color: white;" @click="getrouter()">确认信息</button>
		<text>\n</text>
		<view class="demo">
			<text>默认信息:\n\n姓名:{{name}}\n学号:{{number}}\n专业:{{major}} </text>

		</view>
		<view style="width: 800rpx;"></view>
		<view class="tec">
			<text>马上要离开学校了\n决定将软件开源给学弟学妹们\n这将是最后一次维护\nhttps://github.com/lbzz1906/dont_ps.git\n\n</text>
			<text style="color: red;font-size: 20px;">声明:\n该软件仅用于学术交流,\n请于24小时之内删除\n\n\n\n</text>
		</view>
		</uni-card>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				name: '张伟',
				number: 201721666,
				major: '软件工程',
				stua: true
				
			}
		},
		onLoad() {

		},
		methods: {
			getrouter() {
				let obj = {
					name: this.name,
					number: this.number,
					major: this.major,
					stua: this.stua
				};
				let item = encodeURIComponent(JSON.stringify(obj))
				uni.navigateTo({
					url: '../show/show?item=' + item
				})
			},
			dataClick() {
				this.stua = !this.stua
			}
		}
	}
</script>

<style>
	input {
		margin-top: 10px;
		width: 200px;
		border-bottom: #007AFF 1px solid;
	}

	.tec {
		margin-top: 20px;
		display: flex;
		text-align: center;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.demo {
		border: 2px solid #007AFF;
		border-radius: 10px;
		margin: 0 auto;
		width: 200px;
		text-align: center;
	}
</style>
