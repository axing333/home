<template>
	<div id="header">
		<div class="nav-global">
			<div class="container">
				<h1 class="nav-logo">
					<img src="https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1608471313381&di=c61414fd4cadff45fe453398c9c25df8&imgtype=0&src=http%3A%2F%2Fbpic.588ku.com%2Felement_origin_min_pic%2F00%2F92%2F14%2F2056f1ff3ac6abb.jpg"  style="width:60px;height:60px;padding-left:70px;"alt="">
				</h1>
				<ul class="nav-aside">
					<li class="nav-user">
					  <router-link to="/account">个人中心</router-link>
						<!--active-->
						<div class="nav-user-wrapper">
							<div class="nav-user-list">
								<dl class="nav-user-avatar">
									<dd><span class="ng-scope"></span></dd>
									<dt class="ng-binding"></dt>
								</dl>
								<ul>
									<li class="order"><router-link to="/account" exact>我的订单</router-link></li>
									<!--<li class="support"><a href="javascript:;">售后服务</a></li>
									<li class="coupon"><a href="javascript:;">我的优惠</a></li>
									<li class="information"><a href="javascript:;">账户资料</a></li>-->
									<li class="address"><router-link to="/address">收货地址</router-link></li>
								<!--	<li class="logout"><a href="javascript:;">退出</a></li>-->
								</ul>
							</div>
						</div>
					</li>
					<!--active-->
					<car-panel class="nav-cart"></car-panel>
				</ul>
				<ul class="nav-list">
					<li><a href="javascript:;">在线商城</a>
					<li><a href="javascript:;">相关支持</a></li>
					<li><a href="javascript:;">关于本站</a></li>
					<li><a href="javascript:;">在线客服</a></li>
					<li><a href="javascript:;">帮助</a></li>
					<router-link to="/register" exact tag="li" activeClass="active">
						    <a>注册</a>
						</router-link>
					<router-link to="/login" exact tag="li" activeClass="active">
						    <a>登录</a>
						</router-link>
				</ul>
			</div>
		</div>
		<div class="nav-sub" style="margin-left:430px">
			<div class="nav-sub-wrapper">
				<div class="container">
					<ul class="nav-list">
						<router-link to="/homepage" exact tag="li" activeClass="active">
						    <a>首页</a>
						</router-link>
						<router-link to="/" exact tag="li" activeClass="active">
						    <a>全部商品</a>
						</router-link>
						<li><a href="javascript:;">周边产品</a></li>
						<li><a href="javascript:;">第三方配件</a></li>
						<li><a href="javascript:;">服务</a></li>
						<li></li>
					</ul>
				</div>
			</div>
		</div>
	</div>
</template>
<script>
import CarPanel from '@/components/car-panel'
import Research from '@/components/research.vue'

export default {
  components: {
    CarPanel,
    Research,
    
  }
  
}

</script>

<style >
 

</style>