<template>
	<view class=all>
		<text class="data">{{dateFormatnow()}}</text>
		<image class="door" :src=img mode="aspectFit"></image>
		<view class="mes" style="width: 100%;background-image: url(../../static/mes.jpg);background-size: 100% 100%;">
			<view>
				<text class="regnum">学号:</text>
				<text class="valnum">{{number}}</text>
			</view>
			<view>
				<text class="regname">姓名:</text>
				<text class="valname">{{name}}</text>
			</view>
			<view>
				<text class="regmaj">专业:</text>
				<text class="valmaj">{{major}}</text>
			</view>

		</view>
		<adcell text="123"></adcell>
	</view>

</template>

<script>
	export default {

		data() {
			return {
				time: '',
				number: '',
				name: '',
				major: '',
				stua: true,
				img: ''
			}
		},
		onLoad(option) {
			const item = JSON.parse(decodeURIComponent(option.item));
			this.name = item.name
			this.number = item.number
			this.major = item.major
			if (item.stua == true) {
				this.img = "../../static/in.jpg"
			} else {
				this.img = "../../static/out.jpg"
			}
		},
		mounted: {

		},
		methods: {
			dateFormatnow() {
				var date = new Date();
				var year = date.getFullYear();
				/* 在日期格式中，月份是从0开始的，因此要加0
				 * 使用三元表达式在小于10的前面加0，以达到格式统一  如 09:11:05
				 * */
				var month =
					date.getMonth() + 1 < 10 ?
					"0" + (date.getMonth() + 1) :
					date.getMonth() + 1;
				var day = date.getDate();
				// 拼接
				return (
					year +
					"-" +
					month +
					"-" +
					day
				);
			}
			
		}
	}
</script>

<style>
	.data {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
		color: #ff6666;
		font-size: 50px;
		margin-top: 38px;

	}

	.door {

		flex-direction: column;
		align-items: center;
		justify-content: center;
		width: 100%;
		height: 300px;
		margin-top: 20px;
	}

	.mes {
		height: 200px;
		border: 1px white solid;
	}

	.regnum {
		float: left;
		font-size: 20px;
		display: block;
		margin-top: 24px;
		margin-left: 60px;
	}

	.regname {
		float: left;
		font-size: 20px;
		display: block;
		margin-top: 91px;
		margin-left: -45px;
	}

	.regmaj {
		float: left;
		font-size: 20px;
		display: block;
		margin-top: 160px;
		margin-left: -47px;
	}

	.valnum {
		float: right;
		font-size: 20px;
		display: block;
		margin-top: 24px;
		margin-right: 20px;
	}

	.valname {
		float: right;
		font-size: 20px;
		display: block;
		margin-top: 91px;
		margin-right: -102px;
	}

	.valmaj {
		float: right;
		font-size: 20px;
		display: block;
		right: 0;
		margin-top: 160px;
		margin-right: -102px;
	}
</style>
