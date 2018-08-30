### ajax 

`async [əˈsɪŋk] `

AJAX的全称是Asynchronous JavaScript and XML（异步的 JavaScript 和 XML） 。

```javascript
1.建立xmlHttpRequest对象
if(window.XMLHttpRequest) {
    xmlHttp = new XMLHttpRequest();
    if(xmlHttp.overrideMimeType) {
        xmlHttp.overrideMimeType("text/xml");
    }
} else if(window.ActiveXobject) {
    var activeName = ["MSXML2.XMLHTTP", "Microsoft.XMLHTTP"];
    for(var i = 0; i < activeName.length; i++) {
        try {
            xmlHttp = new ActiveXobject(activeName[i]);
            break;
        } catch(e) {}
    }
}
if(!xmlHttp) {
    alert("创建xmlhttprequest对象失败");
} else {}

2.设置回调函数
   xmlHttp.onreadystatechange= callback;
   function callback(){}

3.使用OPEN方法与服务器建立连接  xmlHttp.open("get","ajax?name="+ name,true)
   此步注意设置http的请求方式（post/get）,如果是POST方式，注意设置请求头信息xmlHttp.setRequestHeader("Content-Type","application/x-www-form-urlencoded")

4.向服务器端发送数据
  xmlHttp.send(null);
  如果是POST方式就不为空
5.在回调函数中针对不同的响应状态进行处理

if(xmlHttp.readyState == 4){       //判断交互是否成功
    if(xmlHttp.status == 200){         //获取服务器返回的数据         //获取纯文本数据
        var responseText =xmlHttp.responseText;
    }
}
```

```javascript
$.ajax({
    type: "post",
    url: url,
    //      data: "para="+para,  此处data可以为 a=1&b=2类型的字符串 或 json数据。
    data: {"para":1},
    cache:false,
    async:false,
    dataType: "json",
    success: function (data ,textStatus, jqXHR){
        if("true"==data.flag){
            alert("合法！");
            return true;
        }else{
            alert("不合法！错误信息如下："+data.errorMsg);
            return false;
        }
    },
    error:function (XMLHttpRequest, textStatus, errorThrown) {      
        alert("请求失败！");
    }
});
```

