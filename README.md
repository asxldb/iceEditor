
# iceEditor富文本编辑器

#### 官方
+ iceEditor 官方网站 [https://www.iceui.net/iceEditor.html](https://www.iceui.net/iceEditor.html)
+ iceEditor 示例文档 [https://www.iceui.net/iceEditor/doc.html](https://www.iceui.net/iceEditor/doc.html)

#### 介绍
iceEditor是一款简约风格的富文本编辑器，体型十分娇小，无任何依赖，整个编辑器只有一个文件，功能却很不平凡！简约的唯美设计，简洁、极速、使用它的时候不需要引用jQuery、font、css……等文件，因为整个编辑器只是一个Js，支持上传图片、附件！支持添加音乐、视频！
iceEditor官方群：324415936

#### 优点
+ 纯原生开发，无任何依赖，冰清玉洁
+ 响应式布局，适应任何分辨率的设备
+ 整个编辑器只有一个文件，高效便捷
+ 简约的唯美设计，简洁、极速

#### 最新更新
# iceEditor v1.1.6
+ **2020-06-20**
+ [修复] textarea内容中的pre代码格式
+ [新增] 新增代码语言（扩展）
+ **2020-06-17**
+ [优化] 添加a链接，可选择新窗口打开
+ [优化] 下拉菜单，点击exec命令菜单后，弹窗消失
+ [优化] 新增pre标签下粘贴代码
+ [优化] 查看源码所造成的一些BUG
+ **2020-06-16**
+ [优化] 编辑内容时，结尾出现多余的p标签
+ [修复] 处于源码视图中，获取到的textarea内容被转义BUG
+ [修复] setValue设置编辑器内容时，如果容器使用的textarea，给它赋值
+ **2020-06-02**
+ [优化] 点击下拉菜单，菜单随之关闭
+ [优化] 删除线功能，取消strike标签（html5已经废弃），改为style样式控制
+ [修改] 创建链接弹窗方式
+ [修改] 添加音乐弹窗方式
# iceEditor v1.1.5
+ **2020-05-29**
+ [新增] QQ、微信……截图直接粘贴功能，默认开启此功能，不需要可关闭，配置项：screenshot
+ [新增] 截图直接上传至服务器功能，默认开启此功能，不需要可关闭，配置项：screenshotUpload
+ [重写] 图片、附件上传的核心方法，由iframe方式改为ajax
+ [修改] upload.php文件，支持存储截图的blob对象
+ **2020-05-22**
+ [修复] 拖拽编辑器的高度时，造成鼠标丢失焦点BUG
+ **2020-05-18**
+ [修复] 视频上传type未定义BUG
+ [修复] 图片上传完成后造成的iframe为空报错
+ [查看其它更新](https://www.iceui.net/iceEditor/update.html) 

#### 提示
[iceui](https://gitee.com/iceui/iceui) 前端框架已经已集成该编辑器。

#### 注意
iceEditor.js的引用禁止放在head标签内，请尽量放在body中或body后面！

#### 使用
```html
<div id="editor"> 欢迎使用iceEditor富文本编辑器 </div>
```
```javascript
//第一步：创建实例化对象
var e = new ice.editor('content');

//第二步：配置图片或附件上传提交表单的路径
//如果你的项目使用的php开发，可直接使用upload.php文件
//其它的编程语言需要你单独处理，后期我会放出.net java等语言代码
//具体与你平常处理multipart/form-data类型的表单一样
//唯一需要注意的就是：处理表单成功后要返回json格式字符串，不能包含其它多余的信息：
//url：文件的地址
//name：文件的名称（包含后缀）
//error：上传成功为0，其它为错误信息，将以弹窗形式提醒用户
//例如批量上传了两张图片：
//[
//	{url:'/upload/img/153444.jpg', name:'153444.jpg', error:0},
//	{url:'/upload/img/153445.jpg', name:'153445.jpg', error:'禁止该文件类型上传'}
//]
e.uploadUrl="/iceEditor/src/upload.php";

//第三步：配置菜单（默认加载全部，无需配置）
e.menu = [
  'backColor',                 //字体背景颜色
  'fontSize',                  //字体大小
  'foreColor',                 //字体颜色
  'bold',                      //粗体
  'italic',                    //斜体
  'underline',                 //下划线
  'strikeThrough',             //删除线
  'justifyLeft',               //左对齐
  'justifyCenter',             //居中对齐
  'justifyRight',              //右对齐
  'indent',                    //增加缩进
  'outdent',                   //减少缩进
  'insertOrderedList',         //有序列表
  'insertUnorderedList',       //无序列表
  'superscript',               //上标
  'subscript',                 //下标
  'createLink',                //创建连接
  'unlink',                    //取消连接
  'hr',                        //水平线
  'table',                     //表格
  'files',                     //附件
  'music',                     //音乐
  'video',                     //视频
  'insertImage',               //图片
  'removeFormat',              //格式化样式
  'code',                      //源码
  'line'                       //菜单分割线
];

//第四步：创建
e.create();
```

#### 设置编辑器尺寸
```javascript
var e = new ice.editor('content');
e.width='700px';   //宽度
e.height='300px';  //高度
e.create();
```

#### 禁用编辑器
```javascript
var e = new ice.editor('content');
e.disabled=true;
e.create();
```

#### 获取内容
```javascript
var e = new ice.editor('content');
console.log(e.getHTML());  //获取HTML格式内容
console.log(e.getText());  //获取Text格式内容
```

#### 设置内容
```javascript
var e = new ice.editor('content');
e.setValue('hello world！');
```

#### 追加内容
```javascript
var e = new ice.editor('content');
e.addValue('hello world！');
```

#### 禁用截图粘贴功能
```javascript
var e = new ice.editor('content');
e.screenshot=false;
```

#### 禁用截图粘贴直接上传功能
```javascript
//禁用后，将默认以base64格式显示图片
var e = new ice.editor('content');
e.screenshotUpload=false;
```

#### 插件开发
```javascript
var e = new ice.editor('content');
e.addValue('hello world！');

//┌────────────────────────────────────────────────────────────────────────
//│ e.plugin(options)传参说明
//│────────────────────────────────────────────────────────────────────────
//│ options     {json}
//│  ├ name     {string}   [必填]菜单唯一的name，可配置menu项显示与顺序
//│  ├ menu     {string}   [必填]展示在菜单栏上的按钮，可为图标或者文字
//│  ├ data     {string}   execCommand的命令
//│  ├ id       {string}   菜单按钮上的id
//│  ├ css      {string}   菜单按钮上的class
//│  ├ style    {string}   该插件的style，以css文件中的样式形式书写
//│  ├ dropdown {string}   下拉菜单里的html，如果定义了popup，则该参数失效
//│  ├ popup    {json} 弹窗json
//│  │    ├ width   {int}    弹窗的宽度
//│  │    ├ height  {int}    弹窗的高度
//│  │    ├ title   {string} 弹窗上的标题
//│  │    └ content {string} 弹窗的内容，可为html
//│  ├ click   {function} 按钮点击事件
//│  └ success {function} 插件安装成功后会自动执行该方法
//└────────────────────────────────────────────────────────────────────────

//下拉菜单类型
e.plugin({
    menu:'代码语言',
    name:'codeLanguages',
    dropdown:`
        <div class="iceEditor-codeLanguages" style="padding:10px 20px;">
            <div>前端请引用iceCode.js</div>
            <select>
                <option disabled selected>代码语言</option>
                <option value ="php">php</option>
                <option value ="js">js</option>
                <option value="html">html</option>
                <option value="java">java</option>
            </select>
        </div>`,
    success:function(e,z){
        //获取content中的按钮
        var select = e.getElementsByTagName('select')[0];
        //设置点击事件
        select.onchange=function(){
            var str = z.getSelectHTML().replace(/<\s*\/p\s*>/ig,"\r\n").replace(/<[^>]+>/ig,'').trim();
            var pre = z.c('pre');
            pre.className = 'iceCode:'+select.value;
            pre.innerHTML = str.length?str:"\r\n";
            z.setHTML(pre,true);
            select.getElementsByTagName('option')[0].selected = true;
        }   
    }
});

//function方式
e.plugin({
	menu:'function方式',
	name:'click',
	click:function(e,z){
		z.setText('hello world');
	}
});
//execCommand命令
e.plugin({
	menu:'删除命令',
	name:'del',
	data:'delete'
});
//下拉菜单类型
e.plugin({
	menu:'下拉菜单',
	name:'dropdown',
	dropdown:'<div class="iceEditor-exec" data="copy" style="padding:10px 20px;">复制选中的文字</div>',
});
//弹出层类型
e.plugin({
	menu:'弹窗演示',
	name:'popup',
	style:'.demo-p{margin-bottom:10px}.demo-button{padding:0 10px}',
	popup:{
		width:230,
		height:120,
		title:'我是一个demo',
		content:'<p class="demo-p">在光标处插入hello world!</p> <button class="demo-button" type="button">确定</button>',
	},
	success:function(e,z){
		//获取content中的按钮
		var btn = e.getElementsByTagName('button')[0];
		//设置点击事件
		btn.onclick=function(){
			z.setText('hello world');
			//关闭本弹窗
			e.close()
		}	
	}
});
e.create();
```