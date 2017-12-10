<template>
	<section class="sectionTan">
		<!-- 地图 -->
		<div id="cesiumMap" class="cesium_map"></div>
		<!-- 弹出框 -->
		<div class="bottom_biao" id="bottom_biao">
			<div class="bottom_biao_top">
				<p>广州市<span>24</span>小时温度预报 当前时间: <span>2017-11-24</span> <span>13:00</span></p>
			</div>
			<div class="bottom_biao_bot">	
				<div id="chartColumn" style="width:100%; height:200px;"></div>
			</div>			
		</div>
		<div class="btnTop">
			<button class="btn_bottom" @click="btnTop">按钮</button>
		</div>
		<!-- 右边栏 -->
		<div class="aside_right">
			<div class="aside_right_top">
				<div class="ri_top">
				   <section class="ri_top_1">
					   <h3>{{city_city}}</h3>
					   <label><img src=""></label>
					   <small>{{date_last}}</small>
				   </section>
				   <section class="ri_top_2">
					   <p>湿度：<span>60%</span></p>
					   <p>温度：<span>16℃</span></p>
					   <p>风速：<span>3级</span></p>
				   </section>				   
				</div>
				<div class="ri_bottom">
				    <ol class="ols">
						<li>
							<h4>周三</h4>
							<h5>11月28日</h5>
							<p class="imsa"><img src="../../../static/images/002.png"></p>
							<p>19~24℃</p>
							<p>多云</p>	
							<p>无持续风微风</p>
						</li>
						<li>
							<h4>周三</h4>
							<h5>11月28日</h5>
							<p class="imsa"><img src="../../../static/images/002.png"></p>
							<p>19~24℃</p>
							<p>多云</p>	
							<p>无持续风微风</p>
						</li>
						<li>
							<h4>周三</h4>
							<h5>11月28日</h5>
							<p class="imsa"><img src="../../../static/images/002.png"></p>
							<p>19~24℃</p>
							<p>多云</p>	
							<p>无持续风微风</p>
						</li>
					</ol>
				</div>
			</div>
			<div class="aside_right_bottom">
				<ul class="uls">
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
					<li><i></i>没开马拉松框架内金拉开门了开门</li>
				</ul>
			</div>
		</div>
		<div class="tanchus">
			<p></p>
			<p></p>
			<p></p>
		</div>
		<!-- 地图弹出框 -->





		<!--工具条-->
		<!-- <el-col :span="24" class="toolbar" style="padding-bottom: 0px;">
			<el-form :inline="true" :model="filters">
				<el-form-item>
					<el-input v-model="filters.name" placeholder="姓名"></el-input>
				</el-form-item>
				<el-form-item>
					<el-button type="primary" v-on:click="getUsers">查询</el-button>
				</el-form-item>
				<el-form-item>
					<el-button type="primary" @click="handleAdd">新增</el-button>
				</el-form-item>
			</el-form>
		</el-col> -->

		<!--列表-->
		<!-- <el-table :data="users" highlight-current-row v-loading="listLoading" @selection-change="selsChange" style="width: 100%;">
			<el-table-column type="selection" width="55">
			</el-table-column>
			<el-table-column type="index" width="60">
			</el-table-column>
			<el-table-column prop="name" label="姓名" width="120" sortable>
			</el-table-column>
			<el-table-column prop="sex" label="性别" width="100" :formatter="formatSex" sortable>
			</el-table-column>
			<el-table-column prop="age" label="年龄" width="100" sortable>
			</el-table-column>
			<el-table-column prop="birth" label="生日" width="120" sortable>
			</el-table-column>
			<el-table-column prop="addr" label="地址" min-width="180" sortable>
			</el-table-column>
			<el-table-column label="操作" width="150">
				<template scope="scope">
					<el-button size="small" @click="handleEdit(scope.$index, scope.row)">编辑</el-button>
					<el-button type="danger" size="small" @click="handleDel(scope.$index, scope.row)">删除</el-button>
				</template>
			</el-table-column>
		</el-table> -->

		<!--工具条-->
		<!-- <el-col :span="24" class="toolbar">
			<el-button type="danger" @click="batchRemove" :disabled="this.sels.length===0">批量删除</el-button>
			<el-pagination layout="prev, pager, next" @current-change="handleCurrentChange" :page-size="20" :total="total" style="float:right;">
			</el-pagination>
		</el-col> -->

		<!--编辑界面-->
		<!-- <el-dialog title="编辑" v-model="editFormVisible" :close-on-click-modal="false">
			<el-form :model="editForm" label-width="80px" :rules="editFormRules" ref="editForm">
				<el-form-item label="姓名" prop="name">
					<el-input v-model="editForm.name" auto-complete="off"></el-input>
				</el-form-item>
				<el-form-item label="性别">
					<el-radio-group v-model="editForm.sex">
						<el-radio class="radio" :label="1">男</el-radio>
						<el-radio class="radio" :label="0">女</el-radio>
					</el-radio-group>
				</el-form-item>
				<el-form-item label="年龄">
					<el-input-number v-model="editForm.age" :min="0" :max="200"></el-input-number>
				</el-form-item>
				<el-form-item label="生日">
					<el-date-picker type="date" placeholder="选择日期" v-model="editForm.birth"></el-date-picker>
				</el-form-item>
				<el-form-item label="地址">
					<el-input type="textarea" v-model="editForm.addr"></el-input>
				</el-form-item>
			</el-form>
			<div slot="footer" class="dialog-footer">
				<el-button @click.native="editFormVisible = false">取消</el-button>
				<el-button type="primary" @click.native="editSubmit" :loading="editLoading">提交</el-button>
			</div>
		</el-dialog> -->

		<!--新增界面-->
		<!-- <el-dialog title="新增" v-model="addFormVisible" :close-on-click-modal="false">
			<el-form :model="addForm" label-width="80px" :rules="addFormRules" ref="addForm">
				<el-form-item label="姓名" prop="name">
					<el-input v-model="addForm.name" auto-complete="off"></el-input>
				</el-form-item>
				<el-form-item label="性别">
					<el-radio-group v-model="addForm.sex">
						<el-radio class="radio" :label="1">男</el-radio>
						<el-radio class="radio" :label="0">女</el-radio>
					</el-radio-group>
				</el-form-item>
				<el-form-item label="年龄">
					<el-input-number v-model="addForm.age" :min="0" :max="200"></el-input-number>
				</el-form-item>
				<el-form-item label="生日">
					<el-date-picker type="date" placeholder="选择日期" v-model="addForm.birth"></el-date-picker>
				</el-form-item>
				<el-form-item label="地址">
					<el-input type="textarea" v-model="addForm.addr"></el-input>
				</el-form-item>
			</el-form>
			<div slot="footer" class="dialog-footer">
				<el-button @click.native="addFormVisible = false">取消</el-button>
				<el-button type="primary" @click.native="addSubmit" :loading="addLoading">提交</el-button>
			</div>
		</el-dialog> -->
	</section>
</template>

<script>
	import util from '../../common/js/util'
	import echarts from 'echarts'
	// import Cesium from 'Cesium'
	
	//import NProgress from 'nprogress'
	import { getUserListPage, removeUser, batchRemoveUser, editUser, addUser } from '../../api/api';

	export default {
		data() {
			return {
				chartColumn: null,
				btnTopFlag: false,
				filters: {
					name: ''
				},
				users: [],
				total: 0,
				page: 1,
				listLoading: false,
				sels: [],//列表选中列

				editFormVisible: false,//编辑界面是否显示
				editLoading: false,
				editFormRules: {
					name: [
						{ required: true, message: '请输入姓名', trigger: 'blur' }
					]
				},
				//编辑界面数据
				editForm: {
					id: 0,
					name: '',
					sex: -1,
					age: 0,
					birth: '',
					addr: ''
				},

				addFormVisible: false,//新增界面是否显示
				addLoading: false,
				addFormRules: {
					name: [
						{ required: true, message: '请输入姓名', trigger: 'blur' }
					]
				},
				//新增界面数据
				addForm: {
					name: '',
					sex: -1,
					age: 0,
					birth: '',
					addr: ''
				},
				city_city: '',
				date_last: '',
				AllDatas: {
					"status": "OK",
					"weather": [
						{
							"city_name": "广州",
							"city_id": "CHGD000000",
							"last_update": "2017-12-08T22:50:00+08:00",
							"now": {
								"text": "晴",
								"code": "1",
								"temperature": "9",
								"feels_like": "8",
								"wind_direction": "北",
								"wind_speed": "12.24",
								"wind_scale": "3",
								"humidity": "73",
								"visibility": "12.70",
								"pressure": "1015",
								"pressure_rising": "未知",
								"air_quality": {
									"city": {
										"aqi": "68",
										"pm25": "49",
										"pm10": "75",
										"so2": "16",
										"no2": "43",
										"co": "0.764",
										"o3": "92",
										"last_update": "2017-12-08T20:00:00+08:00",
										"quality": "良"
									},
									"stations": null
								},
								"alarms": []
							},
							"today": {
								"sunrise": "06:56 AM",
								"sunset": "05:42 PM",
								"suggestion": {
									"dressing": {
										"brief": "较舒适",
										"details": "建议着薄外套、开衫牛仔衫裤等服装。年老体弱者应适当添加衣物，宜着夹克衫、薄毛衣等。"
									},
									"uv": {
										"brief": "中等",
										"details": "属中等强度紫外线辐射天气，外出时建议涂擦SPF高于15、PA+的防晒护肤品，戴帽子、太阳镜。"
									},
									"car_washing": {
										"brief": "较适宜",
										"details": "较适宜洗车，未来一天无雨，风力较小，擦洗一新的汽车至少能保持一天。"
									},
									"travel": {
										"brief": "适宜",
										"details": "天气较好，温度适宜，是个好天气哦。这样的天气适宜旅游，您可以尽情地享受大自然的风光。"
									},
									"flu": {
										"brief": "易发",
										"details": "天冷空气湿度大且昼夜温差也很大，易发生感冒，请注意适当增减衣服。"
									},
									"sport": {
										"brief": "较适宜",
										"details": "天气较好，户外运动请注意防晒。推荐您进行室内运动。"
									}
								}
							},
							"future": [
								{
									"date": "2017-12-08",
									"high": "20",
									"low": "9",
									"day": "周五",
									"text": "多云/晴",
									"code1": "4",
									"code2": "1",
									"cop": "",
									"wind": "风力4级"
								},
								{
									"date": "2017-12-09",
									"high": "19",
									"low": "9",
									"day": "周六",
									"text": "晴/晴",
									"code1": "0",
									"code2": "1",
									"cop": "",
									"wind": "风力2级"
								},
								{
									"date": "2017-12-10",
									"high": "21",
									"low": "10",
									"day": "周日",
									"text": "晴/晴",
									"code1": "0",
									"code2": "1",
									"cop": "",
									"wind": "风力2级"
								},
								{
									"date": "2017-12-11",
									"high": "21",
									"low": "10",
									"day": "周一",
									"text": "晴/阴",
									"code1": "0",
									"code2": "9",
									"cop": "",
									"wind": "风力2级"
								},
								{
									"date": "2017-12-12",
									"high": "20",
									"low": "11",
									"day": "周二",
									"text": "阴/小雨",
									"code1": "9",
									"code2": "13",
									"cop": "",
									"wind": "风力2级"
								},
								{
									"date": "2017-12-13",
									"high": "18",
									"low": "13",
									"day": "周三",
									"text": "小雨/小雨",
									"code1": "13",
									"code2": "13",
									"cop": "",
									"wind": "风力3级"
								},
								{
									"date": "2017-12-14",
									"high": "17",
									"low": "14",
									"day": "周四",
									"text": "小雨/小雨",
									"code1": "13",
									"code2": "13",
									"cop": "",
									"wind": "风力2级"
								},
								{
									"date": "2017-12-15",
									"high": "21",
									"low": "14",
									"day": "周五",
									"text": "小雨/阴",
									"code1": "13",
									"code2": "9",
									"cop": "",
									"wind": "风力2级"
								},
								{
									"date": "2017-12-16",
									"high": "19",
									"low": "11",
									"day": "周六",
									"text": "小雨/多云",
									"code1": "13",
									"code2": "4",
									"cop": "",
									"wind": "风力2级"
								},
								{
									"date": "2017-12-17",
									"high": "16",
									"low": "8",
									"day": "周日",
									"text": "阴/阴",
									"code1": "9",
									"code2": "9",
									"cop": "",
									"wind": "风力3级"
								}
							]
						}
					]
				}

			}
		},
		created () {
			this.getAllData();
		},
		methods: {
			//获取数据
			getAllData(){
				console.log(this.AllDatas.weather[0]);
				this.city_city = this.AllDatas.weather[0].city_name;
				this.date_last = this.AllDatas.weather[0].last_update;

				// this.$axios.get('http://tj.nineton.cn/Heart/index/all?city=CHGD000000').then((data)=>{
				// 	console.log(data)
				// 	this.city_city = data.data.city;
				// })
			},
			//点击向上弹出
			btnTop(){
				var heights = $("#bottom_biao").height()
				if (heights == 0 ) {
					// $("#bottom_biao").css({'height': 'auto'});
					$("#bottom_biao").animate({'height': '200'},1000)
					$(".btnTop").animate({'bottom': '200'},1000)					
				} else {
					// $("#bottom_biao").css({'height': 0})
					$("#bottom_biao").animate({'height': 0},1000)
					$(".btnTop").animate({'bottom': 0},1000)										
				}
			},
			//表格
			drawColumnChart() {
			   this.chartColumn = echarts.init(document.getElementById('chartColumn'));
                var option = {
                    color: ['#3398DB'],
                    tooltip : {
                        trigger: 'axis',
                        axisPointer : {            // 坐标轴指示器，坐标轴触发有效
                            type : 'shadow'        // 默认为直线，可选为：'line' | 'shadow'
                        }
                    },
                    grid: { 
                        left: '3%',
                        right: '4%',
                        bottom: '3%',
                        containLabel: true
                    },
                    xAxis : [
                        {
                            type : 'category',
                            data : ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],
                            axisTick: {
                                alignWithLabel: true
                            }
                        }
                    ],
                    yAxis : [
                        {
                            type : 'value'
                        }
                    ],
                    series : [
                        {
                            name:'直接访问',
                            type:'bar',
                            barWidth: '60%',
                            data:[10, 52, 200, 334, 390, 330, 220]
                        }
                    ]
                };

                this.chartColumn.setOption(option);
			},
			drawCharts() {
                this.drawColumnChart()
            
            },
			//性别显示转换
			// formatSex: function (row, column) {
			// 	return row.sex == 1 ? '男' : row.sex == 0 ? '女' : '未知';
			// },
			handleCurrentChange(val) {
				this.page = val;
				this.getUsers();
			},
			//获取用户列表
			getUsers() {
				let para = {
					page: this.page,
					name: this.filters.name
				};
				this.listLoading = true;
				//NProgress.start();
				getUserListPage(para).then((res) => {
					this.total = res.data.total;
					this.users = res.data.users;
					this.listLoading = false;
					//NProgress.done();
				});
			},
			//删除
			handleDel: function (index, row) {
				this.$confirm('确认删除该记录吗?', '提示', {
					type: 'warning'
				}).then(() => {
					this.listLoading = true;
					//NProgress.start();
					let para = { id: row.id };
					removeUser(para).then((res) => {
						this.listLoading = false;
						//NProgress.done();
						this.$message({
							message: '删除成功',
							type: 'success'
						});
						this.getUsers();
					});
				}).catch(() => {

				});
			},
			//显示编辑界面
			handleEdit: function (index, row) {
				this.editFormVisible = true;
				this.editForm = Object.assign({}, row);
			},
			//显示新增界面
			handleAdd: function () {
				this.addFormVisible = true;
				this.addForm = {
					name: '',
					sex: -1,
					age: 0,
					birth: '',
					addr: ''
				};
			},
			//编辑
			editSubmit: function () {
				this.$refs.editForm.validate((valid) => {
					if (valid) {
						this.$confirm('确认提交吗？', '提示', {}).then(() => {
							this.editLoading = true;
							//NProgress.start();
							let para = Object.assign({}, this.editForm);
							para.birth = (!para.birth || para.birth == '') ? '' : util.formatDate.format(new Date(para.birth), 'yyyy-MM-dd');
							editUser(para).then((res) => {
								this.editLoading = false;
								//NProgress.done();
								this.$message({
									message: '提交成功',
									type: 'success'
								});
								this.$refs['editForm'].resetFields();
								this.editFormVisible = false;
								this.getUsers();
							});
						});
					}
				});
			},
			//新增
			addSubmit: function () {
				this.$refs.addForm.validate((valid) => {
					if (valid) {
						this.$confirm('确认提交吗？', '提示', {}).then(() => {
							this.addLoading = true;
							//NProgress.start();
							let para = Object.assign({}, this.addForm);
							para.birth = (!para.birth || para.birth == '') ? '' : util.formatDate.format(new Date(para.birth), 'yyyy-MM-dd');
							addUser(para).then((res) => {
								this.addLoading = false;
								//NProgress.done();
								this.$message({
									message: '提交成功',
									type: 'success'
								});
								this.$refs['addForm'].resetFields();
								this.addFormVisible = false;
								this.getUsers();
							});
						});
					}
				});
			},
			selsChange: function (sels) {
				this.sels = sels;
			},
			//批量删除
			batchRemove: function () {
				var ids = this.sels.map(item => item.id).toString();
				this.$confirm('确认删除选中记录吗？', '提示', {
					type: 'warning'
				}).then(() => {
					this.listLoading = true;
					//NProgress.start();
					let para = { ids: ids };
					batchRemoveUser(para).then((res) => {
						this.listLoading = false;
						//NProgress.done();
						this.$message({
							message: '删除成功',
							type: 'success'
						});
						this.getUsers();
					});
				}).catch(() => {

				});
			},
			//创建cesium地图
			creatCesiumMap: function () {
				// console.log(Cesium);
				var imageryProviderViewModels = []; 				
				imageryProviderViewModels.push(new Cesium.ProviderViewModel({
					name: 'Mapbox Streets',
					tooltip: 'Mapbox streets',
					iconUrl: Cesium.buildModuleUrl('Widgets/Images/ImageryProviders/mapboxTerrain.png'),
					creationFunction: function() {
						return new Cesium.MapboxImageryProvider({
							mapId: 'mapbox.streets'
						});
					}
				}));
				// imageryProviderViewModels.push(
				// 	new Cesium.ProviderViewModel({
				// 		name : '地图',
				// 		iconUrl : Cesium.buildModuleUrl('Widgets/Images/ImageryProviders/GaoDeStreet.png'),
				// 		tooltip : '交通地图层',
				// 		creationFunction : function() {
				// 			var gaoDeJiaoTongImageryProvider = new Cesium.UrlTemplateImageryProvider({
				// 				url : 'http://webrd0{s}.is.autonavi.com/appmaptile?lang=zh_cn&size=1&scale=1&style=8&x={x}&y={y}&z={z}',
				// 				enablePickFeatures : false,
				// 				//tilingScheme: new GeographicTilingScheme(),
				// 				minimumLevel: 3,
				// 				maximumLevel: 18,
				// 				credit: '北京怡孚和融科技有限公司',
				// 				subdomains: ["1", "2", "3", "4"]
				// 			});
				// 			return gaoDeJiaoTongImageryProvider;
				// 		}
				// 	})
				// );
				// imageryProviderViewModels.push(
				// 	new Cesium.ProviderViewModel({
				// 		name : '影像',
				// 		iconUrl : Cesium.buildModuleUrl('Widgets/Images/ImageryProviders/GaoDeImage.png'),
				// 		tooltip : '影像地图层',
				// 		creationFunction : function() {
				// 			var gaoDeYingXiangImageryProvider = new Cesium.UrlTemplateImageryProvider({
				// 				url : 'http://webst0{s}.is.autonavi.com/appmaptile?style=6&x={x}&y={y}&z={z}',
				// 				pickFeaturesUrl: 'http://webst0{s}.is.autonavi.com/appmaptile?style=8&x={x}&y={y}&z={z}',
				// 				enablePickFeatures : false,
				// 				//tilingScheme: new GeographicTilingScheme(),
				// 				minimumLevel: 3,
				// 				maximumLevel: 18,
				// 				credit: '北京怡孚和融科技有限公司',
				// 				subdomains: ["1", "2", "3", "4"]
				// 			});
				// 			var gaoDeYingXiangMiaoShuImageryProvider = new Cesium.UrlTemplateImageryProvider({
				// 				url : 'http://webst0{s}.is.autonavi.com/appmaptile?style=8&x={x}&y={y}&z={z}',
				// 				enablePickFeatures : false,
				// 				//tilingScheme: new GeographicTilingScheme(),
				// 				minimumLevel: 3,
				// 				maximumLevel: 18,
				// 				credit: '北京怡孚和融科技有限公司',
				// 				subdomains: ["1", "2", "3", "4"]
				// 				});
				// 			return [gaoDeYingXiangImageryProvider,gaoDeYingXiangMiaoShuImageryProvider];
				// 		}
				// 	})
				// );
				var terrainProviderViewModels = [];
				terrainProviderViewModels.push(
					new Cesium.ProviderViewModel({
						name : 'WGS84 椭球体模型',
						iconUrl : Cesium.buildModuleUrl('Widgets/Images/TerrainProviders/Ellipsoid.png'),
						tooltip : 'WGS84 standard ellipsoid, also known as EPSG:4326',
						creationFunction : function() {
							return new Cesium.EllipsoidTerrainProvider();
						}
					})
				);	
				//设置相机默认可视范围，广州省
				Cesium.Camera.DEFAULT_VIEW_RECTANGLE = Cesium.Rectangle.fromDegrees(108.976749,20.230648,117.347519,25.421379);
				//初始化视图对象
				let viewer = new Cesium.Viewer('cesiumMap',{
					animation: false,
					geocoder: false,
					homeButton: true,
					timeline: false,
					sceneModePicker: true,
					baseLayerPicker: true,
					navigationHelpButton: false,
					imageryProviderViewModels: imageryProviderViewModels,
					terrainProviderViewModels: [],
					selectedImageryProviderViewModel: imageryProviderViewModels[0],
					selectedTerrainProviderViewModel: terrainProviderViewModels[0],	
					sceneMode: Cesium.SceneMode.SCENE3D
				});
				viewer.sceneModePicker.viewModel.tooltipColumbusView = "2.5D";
				viewer.homeButton.viewModel.tooltip = "默认视图";
				viewer.homeButton.viewModel._command = Cesium.createCommand(function(){
					viewer.camera.flyTo({			
						destination : Cesium.Camera.DEFAULT_VIEW_RECTANGLE,
						orientation : {
							heading : Cesium.Math.toRadians(0.0),
							pitch : Cesium.Math.toRadians(-90.0),
							roll : 0.0
						}
					});
				});	
				//去除版权信息
				viewer._cesiumWidget._creditContainer.style.display = "none";	
				//infobox iframe 设置运行执行脚本
				var iframe = document.getElementsByClassName('cesium-infoBox-iframe')[0];
				iframe.setAttribute('sandbox', 'allow-same-origin allow-scripts allow-popups allow-forms');
				//
				let pinBuilder = new Cesium.PinBuilder();
				//
				viewer.entities.add({
					id : "A",
					name : 'Question mark',
					position : Cesium.Cartesian3.fromDegrees(113.25872,23.144879),
					billboard : {
						image : pinBuilder.fromText('A', Cesium.Color.AQUAMARINE, 48).toDataURL(),
						verticalOrigin : Cesium.VerticalOrigin.BOTTOM
					}
				});
				viewer.entities.add({
					id : "B",
					name : 'Question mark',
					position : Cesium.Cartesian3.fromDegrees(113.25972,23.144879),
					billboard : {
						image : pinBuilder.fromText('A', Cesium.Color.AQUAMARINE, 48).toDataURL(),
						verticalOrigin : Cesium.VerticalOrigin.BOTTOM
					}
				});
				viewer.entities.add({
					id : "C",
					name : 'Question mark',
					position : Cesium.Cartesian3.fromDegrees(113.26072,23.144879),
					billboard : {
						image : pinBuilder.fromText('A', Cesium.Color.AQUAMARINE, 48).toDataURL(),
						verticalOrigin : Cesium.VerticalOrigin.BOTTOM
					}
				});
				//entity click event bind
				let scene = viewer.scene;
				let camera = viewer.camera;
				let handler = new Cesium.ScreenSpaceEventHandler(scene.canvas);
				handler.setInputAction(function(click) {
					var pickedObject = scene.pick(click.position);
					if (Cesium.defined(pickedObject) && pickedObject.id !== "") {
					//选中对象，根据id请求数据并执行逻辑
					console.log(pickedObject);
					console.log(pickedObject.id.id);
					console.log("id");
						$(".tanchus").show();
					
					}
				}, Cesium.ScreenSpaceEventType.LEFT_CLICK);

			}
		},
		mounted() {
			this.getUsers();
			this.drawCharts();
			this.creatCesiumMap();
		},
        updated () {
            this.drawCharts()
        }
	}

</script>

<style scoped lang="scss">
.sectionTan{
	width: 100%;
	height: 100%;
	position: relative;
	overflow: hidden;
	position: relative;
}
.cesium_map{
	width: 100%;
	height: 100%;
}
.bottom_biao{
  width:100%;
  height: 0;
  background: rgba(255, 255, 255, .8);
  position: absolute;
  left:0;
  bottom:0;
  z-index: 10;
}
 .btnTop{
	position: absolute;
	left:50%;
	bottom:0.2%;
	margin:0 auto;
	z-index: 15;
} 
.btn_bottom{
	background:purple;	
	padding:5px 13px;
}
.aside_right{
   width:20%;
   height:100%;
   background:purple;
   position: absolute;
   top:0;
   right:0;
}
.aside_right_top{
	height:40%;
	// background:orange;
	color:#fff;
	.ri_top{
	   width:100%;
	   height:30%;
	//    background:yellow;
	   border-top:2px solid #ccc;
	   border-bottom:2px solid #ccc;
		.ri_top_1{
		   width:60%;
		   height:100%;
		   float:left;
		//    background:red;
		   position: relative;
		   		   
		   h3{
			 padding:6% 0 0 10%;
			 color:#fff;			 
		   }
		   small{
			 position: absolute;
			 left:10%;
			 bottom:5%;
			 color:#fff;
		   }
		}
		.ri_top_2{
		   width:40%;
		   height:100%;
		   float:left;
		//    background:purple;
		   text-align:left;
		   padding-left:2%;
		   padding-top:2%;		   
		   p{
			 padding:3%;
			 color:#fff;
		   }
		}
	}
	.ri_bottom{
	  width: 100%;
	  height:100%;
	  border-bottom:2px solid green;
	  	.ols{
		  display: flex;
		  text-align:center;
		  li{
			 flex-grow:1;
			 h4{
			   padding:4% 0;
			 }
			 h5{
			   padding:4% 0;
			 }
			 p{
				padding:5% 0;
				display:block;
			 }
			 .imsa{
			   display: block;
			   width:50px;
			   height:50px;
			   margin-left:20%;
			//    background:#ccc;
			     &>img{
					 width: 100%;
					 height:100%; 
				 }
			 }
		  }
		}
	}
}
.aside_right_bottom{
	height:60%;
	background:#ccc;
}

.uls li{
  padding:2.5% 0 2.5% 6%;
  font-size:18px;
  overflow:hidden;
}
.tanchus{
	display: none;
	position:absolute;
	left:3%;
	top:5%;
	width:400px;
	height:260px;
	border:3px solid red;
}
</style>