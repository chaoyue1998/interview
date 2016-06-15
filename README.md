# 前端面试题
	1 变量作用域
		(1) this指向
			var n=2
			var obj={
				n:1,
				func:function(){
				console.log(this.n)
				}
			}
			obj.func()
			var fc=obj.func
			fc()
		(2) setTimeout中this指向
			for(var i=0;i<3;i++){
				setTimeout(function(){console.log(i)},20)
			}
		(3) 如何改变this指向
	2 继承
		(1) call apply
			function a(aa){
				this.aa=aa
			}
			function b(bb,aa){
				this.bb=bb;
				a.apply(this,aa)
			}
			new b(1,[2])
		(2)prototype
			function Shape() {}
			function Rect() {}
			// 方法1
			Rect.prototype = new Shape();
			Rect.prototype.constructor = Shape;
			
			// 方法2
			Rect.prototype = Shape.prototype;
			Rect.prototype.constructor = Shape;
			
			// 方法3
			Rect.prototype = Object.create(Shape.prototype);
			Rect.prototype.area = function () {
			  // do something
			};

	3 安全
		(1) xss
		(2) crsf
	4 性能优化
		(1) 静态资源优化
		(2) js
	5 跨域
		jsonp iframe postmessage
	6 构造函数
		var a={x:2}
		function aa(a){
		  a.x=1 //改变引用对象的属性
		  a={} //改变引用的对象
		  console.log(a)
		}
		aa(a)
		//Object {}
		console.log(a)
		//Object {x: 1}
	7 cookis session localStotage
		同源文档可以读取并修改localStorage数据，sessionStorage只允许同一个窗口下的文档访问，如通过iframe引入的同源文档。
	8 mvc mvp mvvc
		(1) mvc
			View 传送指令到 Controller
			Controller 完成业务逻辑后，要求 Model 改变状态
			Model 将新的数据发送到 View，用户得到反馈
		(2) mvp
			各部分之间的通信，都是双向的，View 与 Model 不发生联系，都通过 Presenter 传递
		(3) mvvc
			采用双向绑定（data-binding）：View的变动，自动反映在 ViewModel，反之亦然。
