#layDate日历插件(非响应式版)
 基于原生JavaScript精心雕琢，兼容了包括IE6在内的所有主流浏览器。她具备优雅的内部代码，良好的性能体验，和完善的皮肤体系。
####官方地址：http://laydate.layui.com/

##兼容性

* ie6+
* Chrome 8+


##样例：

###1、使用步骤
* 引入样式文件

```javascript
<link href="style/calendar.css" rel="stylesheet" type="text/css" />
```
* 在页面头部引用Jquery库：jquery.min.js；

```javascript
<script type="text/javascript" src="javascript/jquery.min.js"></script>
```
 
* 在页面上配置使用参数：

```javascript
    !function(){
    	laydate.skin('default');//切换皮肤，请查看skins下面皮肤库
		laydate({elem: '#demo'});//绑定元素
	}();
	
	//单个时间
	var single = {
		elem: '#single',
		fixed: true,
		istime: true,
		istoday: true,
		format: 'YYYY-MM-DD hh:mm:ss'
	};
	
	//日期范围限制
	var start = {
		elem: '#start',
		fixed: true,
		format: 'YYYY-MM-DD',
		//min: laydate.now(), //设定最小日期为当前日期
		max: '2099-06-16', //最大日期
		istime: false,
		istoday: false,
		choose: function(datas){
			 end.min = datas; //开始日选好后，重置结束日的最小日期
			 end.start = datas; //将结束日的初始值设定为开始日
		}
	};
	
	var end = {
		elem: '#end',
		fixed: true,
		format: 'YYYY-MM-DD',
		//min: laydate.now(),
		max: '2099-06-16',
		istime: false,
		istoday: false,
		choose: function(datas){
			start.max = datas; //结束日选好后，充值开始日的最大日期
		}
	};
	
	laydate(single);
	laydate(start);
	laydate(end);
```

* 在页面上添加代码

```javascript

<div class="box">
    <div class="demo2">
		<h3>单个日期精确到秒</h3>
		<input placeholder="请输入日期" id="single" class="laydate-icon"/>
	</div>
    <div class="demo3">
		<h3>开始结束时间</h3>
		<div class="inline">
		<input class="laydate-icon" id="start" placeholder="开始时间"/>
        <span>到</span>
		<input class="laydate-icon" id="end" placeholder="结束时间"/>
		</div>
	</div>

</div>
    
```
###2、demo
* [单个日期](http://192.168.14.97:8080/acc/wwp/calendar/)
* [日期范围限制](http://192.168.14.97:8080/acc/wwp/calendar/)

##方法和API
###1、方法
     laydate.skin(lib);  //加载皮肤，参数lib为皮肤名 
     laydate(options);
     
###2、参数说明
     options是一个对象，它包含了以下key: '默认值'
        elem: '#id', //需显示日期的元素选择器
        event: 'click', //触发事件
        format: 'YYYY-MM-DD hh:mm:ss', //日期格式
        istime: false, //是否开启时间选择
        isclear: true, //是否显示清空
        istoday: true, //是否显示今天
        issure: true, 是否显示确认
        festival: true //是否显示节日
        min: '1900-01-01 00:00:00', //最小日期
        max: '2099-12-31 23:59:59', //最大日期
        start: '2014-6-15 23:00:00',    //开始日期
        fixed: false, //是否固定在可视区域
        zIndex: 99999999, //css z-index
        choose: function(dates){ //选择好日期的回调
        }
        
##注意事项
* 将laydate整个文件放至您项目的任意目录，不要移动其文件结构，它们具有完整的依赖体系。
