<template>
	<view class="content">
		<image @click="openUpload" class="logo" src="/static/logo.png"></image>
		<l-file ref="lFile" @up-success="upSuccess"></l-file>
		<view >
			{{path}}
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
				path:""
			}
		},
		mounted() {

		},
		methods: {
			upSuccess(e) {
				console.log(e);
			},
			openUpload() {
				const self=this;
				this.$refs.lFile.upload({
					// #ifdef APP-PLUS
					currentWebview: this.$mp.page.$getAppWebview(),
					// #endif
					url: 'http://weijiao.s.li4.cn//api/shop/goods/upload', //测试地址，记得更换
					name: 'file',
					success:res=>{
						self.path=res;
					}
					//header: {'Content-Type':'类型','Authorization':'token'},
					//...其他参数
				});
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
