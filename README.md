# kindeditor-4.1.10
==
kindEditor编辑器是一个由JS写成的在线编辑器，很多网站或CMS等都有用它，口碑不错，目前最新版本是4.1.10。其实它的用法非常简单:

###一、下载
--
    直接点击“download zip”下载即可

###二、部署
--
解压kindeditor-x.x.x.zip文件，将所有文件上传到您的网站程序目录里，例如：http://您的域名/editor/
您可以根据需求删除以下目录后上传到服务器:<br>
	asp-ASP程序<br>
	asp.net-ASP.NET程序<br>
	php-PHP程序<br>
	sp-JSP程序<br>
	examples-演示文件<br>
在这里我假设放到了plugin目录。

###三、嵌入
--
    在需要加入编辑器的页面的HTML中倒入
```
	<link rel="stylesheet" href="/plugin/kindeditor-4.1.10/themes/default/default.css" />
	<script charset="utf-8" src="/plugin/kindeditor-4.1.10/kindeditor-min.js"></script>
	<script charset="utf-8" src="/plugin/kindeditor-4.1.10/lang/zh_CN.js"></script>
```
然后添加一个输入框<br>
```
	<textarea id="editor_id" name="content"></textarea><br>
```
最后在加入一段JS
```
KindEditor.ready(function(K) {
  window.editor = K.create('#editor_id',{
    cssPath:'/public/plugin/editor/plugins/code/prettify.css',
    uploadJson:'/upload/image.php',
    resizeType :1,
    allowPreviewEmoticons : true,
    allowImageUpload : true,
  });
});
```
好了。到这里你应该已经可以看页面上的编辑器了。
这里我还要说的一点是  K.create的第一个参数就是前面textarea的ID，后面跟的JSON格式的数据保护了该编辑器的很多功能。比如我代码上写的

cssPath是代码样式表，uploadJson是编辑器的图片上传组件的上传地址。

说到上传地址，大家应该还记的在上传服务器之前我叫大家先删掉的几个文件夹吧，选择你的网站的开发语言的目录你可以看到如PHP目录下的upload_json.php文件，它里面主要写了接受图片上传的方法，大家可以改改自己用。后台部分的东西这里就不细讲了。

###四、取值
--
    编辑器嵌入完成后我们如何取值呢？其实它的包里也有例字，那就是  用editor.html()方法来取值。
    
kindeditor-4.1.10用法介绍：
    
###一、asp添加编辑器<br/>
####1、在该HTML页面添加以下脚本，注意红色代码路径：
```
  <link rel="stylesheet" href=" kindeditor/themes/default/default.css" />
  <script charset="utf-8" src="kindeditor/kindeditor.js"></script>
  <script charset="utf-8" src="kindeditor/lang/zh_CN.js"></script>
  <script>
  var editor;
  KindEditor.ready(function(K) {
    editor = K.create('#editor_id');
  });
  </script>
```
注释：不含上传文件功能
```
<link rel="stylesheet" href=" kindeditor/themes/default/default.css" />
<script charset="utf-8" src="kindeditor/kindeditor.js"></script>
<script charset="utf-8" src="kindeditor/lang/zh_CN.js"></script>
<script>
var editor;
KindEditor.ready(function(K) {
  editor = K.create('#editor_id',{
    uploadJson : 'kindeditor/asp/upload_json.asp',
    fileManagerJson : 'kindeditor/asp/file_manager_json.asp',
    allowFileManager : true
  });
});
</script>
```
注释：含有上传文件功能<br/>
####2、在需要显示编辑器的位置添加textarea输入框：
```
<textarea id="editor_id" name="content" style="width:700px;height:300px;">
&lt;strong&gt;HTML内容&lt;/strong&gt;
</textarea>
```
###二、如需要单独调用组件：<br/>
####1、 在已经添加以下脚本下加入：
```
<script charset="utf-8" src="kindeditor/kindeditor.js"></script>
<script charset="utf-8" src="kindeditor/lang/zh_CN.js"></script>
<script>
var editor;
KindEditor.ready(function(K) {
  editor = K.create('#editor_id',{
    uploadJson : 'kindeditor/asp/upload_json.asp',
    fileManagerJson : 'kindeditor/asp/file_manager_json.asp',
    allowFileManager : true
  });
};
```
     --------------------------注意添加位置和红色代码名称---------------------- 
```
K('#image1').click(function() {
  editor.loadPlugin('image', function() {
    editor.plugin.imageDialog({
    showRemote : false,
    imageUrl : K('#img').val(),
      clickFn : function(url, title, width, height, border, align) {
      K('#img').val(url);
      editor.hideDialog();
      }
    });
  });
});
</script>
```
--------------------------注意添加位置和红色代码名称----------------------


####2在需要显示编辑器的位置添加input输入框：
```
<input type="text" id="img" name="img" value="" size=50 /> <input type="button" id="image1" value="选择图片" />
```
###三、部分脚本代码，更多参照官方演示文档：<br/>

####1、上传图片弹出框
```
<html>
     <head>
            <meta charset="utf-8" />
            <title>ImageDialog Examples</title>
            <link rel="stylesheet" href="../themes/default/default.css" />
            <script src="../kindeditor.js"></script>
            <script src="../lang/zh_CN.js"></script>
            <script>
                   KindEditor.ready(function(K) {
                          var editor = K.editor({
                                 allowFileManager : true
                          });
                          K('#image1').click(function() {
                                 editor.loadPlugin('image', function() {
                                        editor.plugin.imageDialog({
                                               imageUrl : K('#url1').val(),
                                               clickFn : function(url, title, width, height, border, align) {
                                                      K('#url1').val(url);
                                                      editor.hideDialog();
                                               }
                                        });
                                 });
                          });
                          K('#image2').click(function() {
                                 editor.loadPlugin('image', function() {
                                        editor.plugin.imageDialog({
                                               showLocal : false,
                                               imageUrl : K('#url2').val(),
                                               clickFn : function(url, title, width, height, border, align) {
                                                      K('#url2').val(url);
                                                      editor.hideDialog();
                                               }
                                        });
                                 });
                          });
                          K('#image3').click(function() {
                                 editor.loadPlugin('image', function() {
                                        editor.plugin.imageDialog({
                                               showRemote : false,
                                               imageUrl : K('#url3').val(),
                                               clickFn : function(url, title, width, height, border, align) {
                                                      K('#url3').val(url);
                                                      editor.hideDialog();
                                               }
                                        });
                                 });
                          });
                   });
            </script>
     </head>
     <body>
            <p><input type="text" id="url1" value="" /> <input type="button" id="image1" value="选择图片" />（网络图片 + 本地上传）</p>
            <p><input type="text" id="url2" value="" /> <input type="button" id="image2" value="选择图片" />（网络图片）</p>
            <p><input type="text" id="url3" value="" /> <input type="button" id="image3" value="选择图片" />（本地上传）</p>
     </body>
  </html>
``` 
####2、批量上传图片弹出框
```
<html>
     <head>
            <meta charset="utf-8" />
            <title>MultiImageDialog Examples</title>
            <link rel="stylesheet" href="../themes/default/default.css" />
            <script src="../kindeditor.js"></script>
            <script src="../lang/zh_CN.js"></script>
            <script>
                   KindEditor.ready(function(K) {
                          var editor = K.editor({
                                 allowFileManager : true
                          });
                          K('#J_selectImage').click(function() {
                                 editor.loadPlugin('multiimage', function() {
                                        editor.plugin.multiImageDialog({
                                               clickFn : function(urlList) {
                                                      var div = K('#J_imageView');
                                                      div.html('');
                                                      K.each(urlList, function(i, data) {
                                                             div.append('<img src="' + data.url + '">');
                                                      });
                                                      editor.hideDialog();
                                               }
                                        });
                                 });
                          });
                   });
            </script>
     </head>
     <body>
            <input type="button" id="J_selectImage" value="批量上传" />
            <div id="J_imageView"></div>
     </body>
</html>
```
####3、上传文件弹出框
```
<html>
     <head>
            <meta charset="utf-8" />
            <title>fileDialog Examples</title>
            <link rel="stylesheet" href="../themes/default/default.css" />
            <script src="../kindeditor.js"></script>
            <script src="../lang/zh_CN.js"></script>
            <script>
                   KindEditor.ready(function(K) {
                          var editor = K.editor({
                                 allowFileManager : true
                          });
                          K('#insertfile').click(function() {
                                 editor.loadPlugin('insertfile', function() {
                                        editor.plugin.fileDialog({
                                               fileUrl : K('#url').val(),
                                               clickFn : function(url, title) {
                                                      K('#url').val(url);
                                                      editor.hideDialog();
                                               }
                                        });
                                 });
                          });
                   });
            </script>
     </head>
     <body>
            <input type="text" id="url" value="" /> <input type="button" id="insertfile" value="选择文件" />
     </body>
</html>
```
###四、部分脚本修改代码：<br/>
####1、插入文件后，显示为路径如需修改为显示图标，在<br/>
kindeditor/plugins/insertfile/insertfile.js文件中把：
```
self.clickToolbar(name, function() {
            self.plugin.fileDialog({
                   clickFn : function(url, title) {
                          var html = '<a class="ke-insertfile" href="' + url + '" data-ke-src="' + url + '" target="_blank">' + title + '</a>';
                          self.insertHtml(html).hideDialog().focus();
                    }
            });
};
```
替换成（注意红色代码路径）：
```
	self.clickToolbar(name, function() {
		self.plugin.fileDialog({
			clickFn : function(url, title) {
					  var ext=/\.[^\.]+$/.exec(url);
					  img = 'rar.gif';
					  if(ext == '.doc')  img='doc.gif';
					  if(ext == '.xls')  img="execl.gif";
					  if(ext == ".ppt")  img="ppt.gif";
					  if(ext ==  ".rar")  img="rar.gif";
					  if(ext ==  ".zip")  img="zip.gif";
					  if(ext ==  ".txt")  img="txt.gif";
					  if(ext ==  ".pdf")  img="pdf.gif";
					  if(ext ==  ".docx") img="doc.gif";
					  if(ext ==  ".xlsx") img="execl.gif";
					  if(ext == ".pptx") img="ppt.gif";
					  img = "/hkdnkjweb2014/SysImage/icon32/"+img;
					  var html ='<a class="ke-insertfile" href="' + url + '" data-ke-src="' + url + '" target="_self">' + '<img src="'+img+'" border="0"/>' +  '</a>';
					  self.insertHtml(html).hideDialog().focus();  
			}
		});
	};
```
