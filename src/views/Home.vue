<template>
	<el-row class="container">
		<el-col :span="24" class="header">
			<el-col :span="14" class="logo" :class="collapsed?'logo-collapse-width':'logo-width'">
				{{collapsed?'':sysName}}
			</el-col>
			<el-col :span="9" class="navlists">
				<!-- <el-col :span="2">
					<div class="tools" @click.prevent="collapse">
						<i class="fa fa-align-justify"></i>
					</div>
				</el-col> -->
				<el-col :span="9" class="navlists1">
				    <router-link to="/table">首页</router-link>
					<router-link to="/form">数据监控</router-link>
					<router-link to="/user">展示分析</router-link>
					<router-link to="/form">质量控制</router-link>
					<router-link to="/user">系统设置</router-link>
			 <!-- <el-select v-model="value2" placeholder="请选择">
					<el-option
					v-for="item in options2"
					:key="item.value"
					:label="item.label"
					:value="item.value"
					:disabled="item.disabled">
					</el-option>
  			  </el-select> -->
					<!--<a href="#">aaa</a>
					<a href="#">bbbb</a>
					<a href="#">cccc</a>
					<a href="#">ddddd</a>
					<a href="#">eeeee</a>-->
				</el-col>	
			</el-col>
			<el-col :span="3" class="userinfo">
				<el-dropdown trigger="hover">
					<span class="el-dropdown-link userinfo-inner"><img :src="this.sysUserAvatar" /> {{sysUserName}}</span>
					<el-dropdown-menu slot="dropdown">
						<el-dropdown-item>我的消息</el-dropdown-item>
						<el-dropdown-item>设置</el-dropdown-item>
						<el-dropdown-item divided @click.native="logout">退出登录</el-dropdown-item>
					</el-dropdown-menu>
				</el-dropdown>
			</el-col>
		</el-col>
		<el-col :span="24" class="main">
			 <!-- <aside :class="collapsed?'menu-collapsed':'menu-expanded'"> -->
				<!--导航菜单-->
				<!-- <el-menu :default-active="$route.path" class="el-menu-vertical-demo" @open="handleopen" @close="handleclose" @select="handleselect"
					 unique-opened router v-show="!collapsed">
					<template v-for="(item,index) in $router.options.routes" v-if="!item.hidden">
						<el-submenu :index="index+''" v-if="!item.leaf">
							<template slot="title"><i :class="item.iconCls"></i>{{item.name}}</template>
							<el-menu-item v-for="child in item.children" :index="child.path" :key="child.path" v-if="!child.hidden">{{child.name}}</el-menu-item>
						</el-submenu>
						<el-menu-item v-if="item.leaf&&item.children.length>0" :index="item.children[0].path"><i :class="item.iconCls"></i>{{item.children[0].name}}</el-menu-item>
					</template>
				</el-menu> -->
				<!--导航菜单-折叠后-->
				<!-- <ul class="el-menu el-menu-vertical-demo collapsed" v-show="collapsed" ref="menuCollapsed">
					<li v-for="(item,index) in $router.options.routes" v-if="!item.hidden" class="el-submenu item">
						<template v-if="!item.leaf">
							<div class="el-submenu__title" style="padding-left: 20px;" @mouseover="showMenu(index,true)" @mouseout="showMenu(index,false)"><i :class="item.iconCls"></i></div>
							<ul class="el-menu submenu" :class="'submenu-hook-'+index" @mouseover="showMenu(index,true)" @mouseout="showMenu(index,false)"> 
								<li v-for="child in item.children" v-if="!child.hidden" :key="child.path" class="el-menu-item" style="padding-left: 40px;" :class="$route.path==child.path?'is-active':''" @click="$router.push(child.path)">{{child.name}}</li>
							</ul>
						</template>
						<template v-else>
							<li class="el-submenu">
								<div class="el-submenu__title el-menu-item" style="padding-left: 20px;height: 56px;line-height: 56px;padding: 0 20px;" :class="$route.path==item.children[0].path?'is-active':''" @click="$router.push(item.children[0].path)"><i :class="item.iconCls"></i></div>
							</li>
						</template>
					</li>
				</ul> -->
			 <!-- </aside> 	 -->
			<!-- <section class="content-container" >
				<div class="grid-content bg-purple-light"> -->
					<!-- <el-col :span="24" class="breadcrumb-container">
						<strong class="title">{{$route.name}}</strong>
						<el-breadcrumb separator="/" class="breadcrumb-inner">
							<el-breadcrumb-item v-for="item in $route.matched" :key="item.path">
								{{ item.name }}
							</el-breadcrumb-item>
						</el-breadcrumb>
					</el-col> -->
					<el-col :span="24" class="content-wrapper">
						<transition name="fade" mode="out-in">
							<router-view></router-view>
						</transition>
					</el-col>
				<!-- </div>
			</section> -->
		</el-col>
		<el-col :span="24" class="footer">
			版权所有：中国气象局广州热带所海洋气象研究所
		</el-col>
	</el-row>
</template>

<script>
	export default {
		data() {
			return {
				sysName:'热带季风区云降水物理观测与分析系统',
				collapsed:false,
				sysUserName: '',
				sysUserAvatar: '',
				form: {
					name: '',
					region: '',
					date1: '',
					date2: '',
					delivery: false,
					type: [],
					resource: '',
					desc: ''
				},
				options2: [{
					value: '选项1',
					label: '黄金糕'
					}, {
					value: '选项2',
					label: '双皮奶',
					disabled: true
					}, {
					value: '选项3',
					label: '蚵仔煎'
					}, {
					value: '选项4',
					label: '龙须面'
					}, {
					value: '选项5',
					label: '北京烤鸭'
					}],
					value2: ''
			}
		},
		methods: {
			onSubmit() {
				console.log('submit!');
			},
			handleopen() {
				//console.log('handleopen');
			},
			handleclose() {
				//console.log('handleclose');
			},
			handleselect: function (a, b) {
			},
			//退出登录
			logout: function () {
				var _this = this;
				this.$confirm('确认退出吗?', '提示', {
					//type: 'warning'
				}).then(() => {
					sessionStorage.removeItem('user');
					_this.$router.push('/login');
				}).catch(() => {

				});


			},
			//折叠导航栏
			collapse:function(){
				this.collapsed=!this.collapsed;
			},
			showMenu(i,status){
				this.$refs.menuCollapsed.getElementsByClassName('submenu-hook-'+i)[0].style.display=status?'block':'none';
			}
		},
		mounted() {
			var user = sessionStorage.getItem('user');
			if (user) {
				user = JSON.parse(user);
				this.sysUserName = user.name || '';
				this.sysUserAvatar = user.avatar || '';
			}

		}
	}

</script>

<style scoped lang="scss">
	@import '~scss_vars';
	
	.container {
		position: absolute;
		top: 0px;
		bottom: 0px;
		width: 100%;
		.header {
			height: 60px;
			line-height: 60px;
			background: $color-primary;
			color:#fff;
			.navlists1{
			   width:100%;
			   height:60px;
			//    background:purple;
			   margin-left:40%;
			   a{
				 padding: 0 3.8%; 
				 color:#fff; 
				//  background:green;
				 text-decoration:none;
				 font-size:20px;
			   }
			}
			.userinfo {
				text-align: right;
				padding-right: 35px;
				float: right;
				width:20%;
				.userinfo-inner {
					cursor: pointer;
					color:#fff;
					img {
						width: 40px;
						height: 40px;
						border-radius: 20px;
						margin: 10px 0px 10px 10px;
						float: right;
					}
				}
			}
			.logo {
				//width:230px;
				// width:490px;
				height:60px;
				font-size: 22px;
				padding-left:40px;
				padding-right:40px;
				border-color: rgba(238,241,146,0.3);
				border-right-width: 1px;
				border-right-style: solid;
				img {
					width: 40px;
					float: left;
					margin: 10px 10px 10px 18px;
				}
				.txt {
					color:#fff;
				}
			}
			.logo-width{
				width:600px;
				// width:40%;
			}
			.logo-collapse-width{
				width:0px;
			}
			.tools{
				padding: 0px 23px;
				width:14px;
				height: 60px;
				line-height: 60px;
				cursor: pointer;
			}
		}
		.main {
			display: flex;
			background: #324057;
			position: absolute;
			top: 60px;
			bottom: 30px;
			overflow: hidden;
			
			// aside {
			// 	flex:0 0 230px;
			// 	width: 230px;
			// 	// position: absolute;
			// 	// top: 0px;
			// 	// bottom: 0px;
			// 	.el-menu{
			// 		height: 100%;
			// 	}
			// 	.collapsed{
			// 		width:60px;
			// 		.item{
			// 			position: relative;
			// 		}
			// 		.submenu{
			// 			position:absolute;
			// 			top:0px;
			// 			left:60px;
			// 			z-index:99999;
			// 			height:auto;
			// 			display:none;
			// 		}

			// 	}
			// }
			// .menu-collapsed{
			// 	flex:0 0 60px;
			// 	width: 60px;
			// }
			// .menu-expanded{
			// 	flex:0 0 230px;
			// 	width: 230px;
			// }
			// .content-container {
				// background: #f1f2f7;
				// flex:1;
				// position: absolute;
				// right: 0px;
				// top: 0px;
				// bottom: 0px;
				// left: 230px;
				// overflow-y: scroll;
				// padding: 0px;
				// .breadcrumb-container {
				// 	//margin-bottom: 15px;
				// 	.title {
				// 		width: 200px;
				// 		float: left;
				// 		color: #475669;
				// 	}
				// 	.breadcrumb-inner {
				// 		float: right;
				// 	}
				// }
				.content-wrapper {
					width:100%;
					height:100%;
					// background-color:green;
					box-sizing: border-box;
				}
			// }
		}
		.footer{
			width: 100%;
			height: 30px;
			background:$color-primary;;
			position: absolute;
			left:0;
			bottom:0;
			overflow:hidden;
			line-height:30px;
			text-align:center;
			font-size:14px;
			font-weight:bold;
			color:#ccc;
		}
		
	}
	
</style>