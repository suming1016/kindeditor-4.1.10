# kindeditor-4.1.10

kindEditor�༭����һ����JSд�ɵ����߱༭�����ܶ���վ��CMS�ȶ����������ڱ�����Ŀǰ���°汾��4.1.10����ʵ�����÷��ǳ���:

һ������

    ֱ�ӵ����download zip�����ؼ���

��������
��ѹkindeditor-x.x.x.zip�ļ����������ļ��ϴ���������վ����Ŀ¼����磺http://��������/editor/
�����Ը�������ɾ������Ŀ¼���ϴ�����������
	asp-ASP����
	asp.net-ASP.NET����
	php-PHP����
	sp-JSP����
	examples-��ʾ�ļ�
�������Ҽ���ŵ���pluginĿ¼��

����Ƕ��

    ����Ҫ����༭����ҳ���HTML�е���

	<link rel="stylesheet" href="/plugin/kindeditor-4.1.10/themes/default/default.css" />
	<script charset="utf-8" src="/plugin/kindeditor-4.1.10/kindeditor-min.js"></script>
	<script charset="utf-8" src="/plugin/kindeditor-4.1.10/lang/zh_CN.js"></script>
Ȼ�����һ�������
	<textarea id="editor_id" name="content"></textarea>
����ڼ���һ��JS
<script>
KindEditor.ready(function(K) {
window.editor = K.create('#editor_id',{
cssPath:'/public/plugin/editor/plugins/code/prettify.css',
uploadJson:'/upload/image.php',
resizeType :1,
allowPreviewEmoticons : true,
allowImageUpload : true,
});
});
</script>
���ˡ���������Ӧ���Ѿ����Կ�ҳ���ϵı༭���ˡ�
�����һ�Ҫ˵��һ����  K.create�ĵ�һ����������ǰ��textarea��ID���������JSON��ʽ�����ݱ����˸ñ༭���ĺܶ๦�ܡ������Ҵ�����д��

cssPath�Ǵ�����ʽ��uploadJson�Ǳ༭����ͼƬ�ϴ�������ϴ���ַ��

˵���ϴ���ַ�����Ӧ�û��ǵ����ϴ�������֮ǰ�ҽд����ɾ���ļ����ļ��аɣ�ѡ�������վ�Ŀ������Ե�Ŀ¼����Կ�����PHPĿ¼�µ�upload_json.php�ļ�����������Ҫд�˽���ͼƬ�ϴ��ķ�������ҿ��Ըĸ��Լ��á���̨���ֵĶ�������Ͳ�ϸ���ˡ�

�ġ�ȡֵ

    �༭��Ƕ����ɺ��������ȡֵ�أ���ʵ���İ���Ҳ�����֣��Ǿ���  ��editor.html()������ȡֵ��
    
--------------------------------------------------------------------------------------------------------------------------------------
kindeditor-4.1.10�÷����ܣ�
    
һ��asp��ӱ༭��
1�ڸ�HTMLҳ��������½ű���ע���ɫ����·����
<link rel="stylesheet" href=" kindeditor/themes/default/default.css" />
<script charset="utf-8" src="kindeditor/kindeditor.js"></script>
<script charset="utf-8" src="kindeditor/lang/zh_CN.js"></script>
<script>
var editor;
KindEditor.ready(function(K) {
editor = K.create('#editor_id');
      });
</script>
ע�ͣ������ϴ��ļ�����
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
ע�ͣ������ϴ��ļ�����
2����Ҫ��ʾ�༭����λ�����textarea�����
<textarea id="editor_id" name="content" style="width:700px;height:300px;">
&lt;strong&gt;HTML����&lt;/strong&gt;
</textarea>
��������Ҫ�������������
1 ���Ѿ�������½ű��¼��룺
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
     --------------------------ע�����λ�úͺ�ɫ��������----------------------                          
K('#image1').click(function() {
editor.loadPlugin('image', function() {
editor.plugin.imageDialog({
showRemote : false,
imageUrl : K('#img').val(),
clickFn : function(url, title, width, height, border, align) {
K('#img').val(url);
editor.hideDialog();
}});});});
     --------------------------ע�����λ�úͺ�ɫ��������----------------------
});
</script>
2����Ҫ��ʾ�༭����λ�����input�����
<input type="text" id="img" name="img" value="" size=50 /> <input type="button" id="image1" value="ѡ��ͼƬ" />

�������ֽű����룬������չٷ���ʾ�ĵ���

1 �ϴ�ͼƬ������
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
<p><input type="text" id="url1" value="" /> <input type="button" id="image1" value="ѡ��ͼƬ" />������ͼƬ + �����ϴ���</p>
<p><input type="text" id="url2" value="" /> <input type="button" id="image2" value="ѡ��ͼƬ" />������ͼƬ��</p>
<p><input type="text" id="url3" value="" /> <input type="button" id="image3" value="ѡ��ͼƬ" />�������ϴ���</p>
</body></html>
     
2 �����ϴ�ͼƬ������
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
<input type="button" id="J_selectImage" value="�����ϴ�" />
<div id="J_imageView"></div>
</body>
</html>

3 �ϴ��ļ�������
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
<input type="text" id="url" value="" /> <input type="button" id="insertfile" value="ѡ���ļ�" />
</body>
</html>

�ġ����ֽű��޸Ĵ��룺
1 �����ļ�����ʾΪ·�������޸�Ϊ��ʾͼ�꣬��
kindeditor/plugins/insertfile/insertfile.js�ļ��аѣ�
self.clickToolbar(name, function() {
self.plugin.fileDialog({
clickFn : function(url, title) {
var html = '<a class="ke-insertfile" href="' + url + '" data-ke-src="' + url + '" target="_blank">' + title + '</a>';
self.insertHtml(html).hideDialog().focus();
}
});
};
�滻�ɣ�ע���ɫ����·������
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
# kindeditor-4.1.10
