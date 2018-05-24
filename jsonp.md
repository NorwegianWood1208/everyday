# jsonp

标签（空格分隔）：jsonp

---

#eval
###eval是用来转换json格式的一种方法
    let s3 = "{'name':'hehe'}";

    //    console.log(eval('('+s3+')'));如果要转换变量，必须字符串拼接起一个括号

#(new Function('参数','return '+s3))()
###new Function原型的方式可以将字符串转化为可使用的方法，前面传入的字符串为参数，最后的字符串为方法体内执行的代码。
    第一种格式：
    let s3 = "{'name':'hehe'}";
    let s4 = (new Function('','return '+s3))();
    console.log(s4);   //{name: "hehe"}
    
    第二种格式：
    var fun1 = new Function ('a', 'return a');  
    console.log( fun1(1) ); //1  


#promise
###第一种是原生的get方法
    t.onblur = function(){
            //这里有两个参数resolve，reject。代表成功和失败
            let pp = new Promise(function(resolve,reject){
                let ajax = new XMLHttpRequest;
                ajax.open('get','/sleep?user='+t.value,true);
                ajax.send();
                ajax.onload = function(){
                    resolve(ajax.responseText);
                }
            });
            这个时候回先弹2，再打印res,最后弹1
            pp.then(function(res){
                console.log(res);
            }).then(function(){
                alert(1);
            });
                alert(2);
        }
        
        
        
###第二种是axios的post方法
    t.onblur = function(){
         axios.post('/post',{name:t.value})
         .then(res => {
             console.log(res.data);
         });
    }

#跨域
##同源:

    同域名、同端口、同协议

##跨源:

    不同域名、不同端口、不同协议
#解决跨域
           
###1.通过高版本的XMLHttpRequest + 后端设置请求头权限

    header('Access-Control-Allow-Origin:*');
    更好用：
    优点：
        一套ajax请求既能够ajax请求也能跨域请求
    缺点:
        低版本用不了
###2.服务器代理
    原理:
        a能访问b,b能访问c，就等同于a能访问c

        a:前端请求
        b:同源下的后端文件
        c:第三方数据 
        比如:http://www.baidu.com
        http://www.kaola.com/getSuggestKeyword.html?query=猫&size=10

        缺点：
            第三如果改了，那么你自动也会改
#jsonp
    json + padding
##说白了：
            前端定义一个全局函数给后端调用
##jsonp:

    1.后端传给前端的数据为函数名 + 括号的 把数据放入括号中
    
    2.前端需要在全局放一个函数去接收
    
    3.当需要数据的时候，动态创建script标签，通过url的方式去访问后端
        script标签又能解析js，所以等同于函数调用

##优点:

    兼容非常好
    let oS = null;
##栗子一枚
    //定义一个全局的函数去接收后端的数据
    function fn(data){
        let html = '';
        console.log(data);
        data.s.forEach(e => {
            html += '<li>'+ e +'</li>'
        });
        ul.innerHTML = html;
        oS.remove();
    }
    /*
        在输入的时候去请求数据
    */
    let url = https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su?wd=
    t.onkeyup = function(){
        oS = document.createElement('script');
        oS.src = url+ t.value +'&cb=fn';
        h.appendChild(oS);
        oS.remove();
    }
    
    
##jsonp库
 

    let url = 'https://sp0.baidu.com/5a1Fazu8AA54nxGko9WTAnF6hhy/su?wd=灭霸'
            fetchJsonp(url,{
                jsonpCallback:'cb'
            }).then(e=>e.json())
            .then(res=>{
                console.log(res);
            });
            
            
    axios不支持跨域
    
    fetchJsonp 支持跨域