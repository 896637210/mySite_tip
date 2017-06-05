# mySite_tip
常用的代码
/**
 * addZero
 * 小于10 前边补0
 */
function addZero(num){
    if(num<10){
        num="0"+num;
    }
    return num;
}
/**窗口中
 * 居中函数
 *
 * element：需要居中的元素
 */
function center(element){
    element.style.left=((getWindowSize().width-element.offsetWidth)/2+getScrollSize().left)+"px";
    element.style.top=((getWindowSize().height-element.offsetHeight)/2+getScrollSize().top)+"px";
}
/**父级元素下
 * 居中函数
 *
 * element：需要居中的元素
 */
function childCenter(element){
        element.style.marginLeft=(element.parentNode.clientWidth-element.offsetWidth)/2+"px";
        element.style.marginTop=(element.parentNode.clientHeight-element.offsetHeight)/2+"px";
}
/**
 *获取窗口尺寸
 * 不同浏览器。窗口的尺寸计算不同
 */
function getWindowSize(){
    return {
    "width":window.innerWidth||document.documentElement.clientWidth,
    "height":window.innerHeight||document.documentElement.clientHeight
    }
}
/**
 * 获取滚动条滚动的值
 */
function getScrollSize(){
    return{
        "top":document.documentElement.scrollTop||document.body.scrollTop,
        "left":document.documentElement.scrollLeft||document.body.scrollLeft
    }
}
//页面加载结束
window.addEventListener("load",function(){

 })
//窗口滚动条滚动
 window.addEventListener("scroll",function(){

 })
 //窗口调整大小
 window.addEventListener("resize",function(){

 })
/**
*小得读取按钮样式
*/
    button{
        width:150px;
        background: green;
    }
    button:after{
        content:"";
        display:inline-block;
        width:5px;
        height:5px;
        /*border:1px solid #fff;*/
        border-radius:5px;
        /*box-shadow: 8px 0 #fff,16px 0 #fff,24px 0 #fff;*/
        animation: dotting infinite 3s step-start;
    }
    @keyframes dotting{
        0%{
            box-shadow:none;
        }
        30%{
            box-shadow:none;
        }
        50%{
            box-shadow: 8px 0 #fff;
        }
        70%{
            box-shadow: 8px 0 #fff,16px 0 #fff;
        }
        90%{
            box-shadow: 8px 0 #fff,16px 0 #fff,24px 0 #fff;
        }
        100%{
            box-shadow: 8px 0 #fff,16px 0 #fff,24px 0 #fff;
        }
    }
 <button>提交中</button>

/**
*显示隐藏地3种方式
*/
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <button></button>
    <br/>
    <img src=" " alt="">
    <script type="text/javascript">
    var btn=document.querySelector("button");
    var img=document.querySelector("img");
        // 常规
        btn.addEventListener("click",function(){
            if(img.style.display=="none"){
                img.style.display="block";
            }else{
                img.style.display="none";
            } ;
        });


        //三元
        btn.addEventListener("click",function(){
            img.style.display=(img.style.display=="none")?"block":"none";
        });   


        //布尔型变量的切换
        var b=true;
        btn.addEventListener("click",function(){
            if(b){
                img.style.display="none";
                b=false;
            }else{
                img.style.display="block";
                b=true;
            } ;
        });


        //switch
        btn.addEventListener("click",function(){
            switch(img.style.display){
                case "":
                img.style.display="none";
                break;
                case "none":
                img.style.display="";
                break;
            };
        });
    </script>
</body>
</html>

/**
*异步  同步  默认时事件
*/
stopPropagation()：阻止事件传递（ie下有差异）
preventDefault();阻止默认动作（ie下有差异）



async 异步
defer加载

/**
*tab基础
*/
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style>
        *{
            padding: 0;
            margin:0;
            list-style: none;
        }
        .tab{

        }
        .tab ul{

        }
        .tab ul:after{
            content: "";
            display: block;
            clear: both;
        }
        .tab ul li{
            float: left;
            width: 100px;
            height: 50px;
            border: 1px solid #ddd;
            margin-left: 10px;
            cursor: pointer;
        }
        .tab ul li.active{
            position: relative;
            top: 5px;
            z-index: 10;
            border: 1px solid green;
            border-bottom: 0;
            background: #fff;
        }
        .tab div{
            height: 200px;
            border: 1px solid green;
            display: none;
        }
        div.spotlight{
            display: block;
            position: relative;
            z-index: 9;
            top: 3px;
            background: #fff;
        }
    </style>
</head>
<body>
    <div class="tab">
        <ul>
            <li class="active"></li>
            <li></li>
            <li></li>
        </ul>
        <div class="spotlight"></div>
        <div></div>
        <div></div>
    </div>
    <script type="text/javascript">
var lis=document.querySelectorAll(".tab ul li");
var divs=document.querySelectorAll(".tab div");
//forEach
lis.forEach(function(v,i){
    v.addEventListener("click",function(){
        //第一步清除所有元素的active;
        lis.forEach(function(v,i){
        v.className="";
        divs[i].className="";
        });
        //为当前的元素添加active;
        v.className="active";
        divs[i].className="spotlight";
    });
});


//setAttribute,getAttribute()
for(var i=0;i<lis.length;i++){
       //循环为每个一个list添加index
      lis[i].setAttribute("index",i);
      lis[i].addEventListener("click",function(){
          for(var j=0;j<lis.length;j++){
              lis[j].className="";
            divs[j].className="";
         };
    divs[this.getAttribute("index")].className="spotlight";
      this.className="active";
    });
};


//匿名函数的自触发
for(var i=0;i<lis.length;i++){
    //循环为每个一个list添加index
    //匿名函数的自触发(形参)(实参)
    (function(index){
        lis[index].addEventListener("click",function(){
            for(var j=0;j<lis.length;j++){
                    lis[j].className="";
                    divs[j].className="";
            } ;
            divs[index].className="spotlight";
            this.className="active";
        });
    })(i);
};
    </script>
</body>
</html>
/**
*pattern 清除空格
*/
<!--
清除空格
 -->

var demo=document.querySelector(".demo");
var str="  a ";
var pattern=/^\s*$/;
demo.addEventListener("keyup",function(){
    trim(this.value);
});
trim(" ");
function trim(value){
    if(/^\s*$/.test(value)){
        value=value.replace(/^\s*$/,"");
    }else if(/^\s*(.+?)\s*$/){
        value=value.replace(/^\s*(.+?)\s*$/,"$1");
    }
    return value;
}

/**
*简单input验证
*/
/**
*注册
*/
        /*保存错误信息*/
        var errorMsg=null;
        /*处理密码强度*/
        pwd.addEventListener("keyup",function(){
            switch (valide_pwd(trim(this.value))) {
                case 3:
                    feedback.innerHTML="密码强度低";
                    errorMsg="密码强度低";
                    break;
                case 2:
                    feedback.innerHTML="密码强度中";
                    errorMsg="密码强度中";
                    break;
                case 1:
                    feedback.innerHTML="密码强度较高";
                    errorMsg="密码强度较高";
                    break;
                case 0:
                    feedback.innerHTML="密码强度高";
                    errorMsg="";
                    break;
                default:
                    // statements_def
                    break;
            }
        })
        /*用户名失去焦点时的验证*/
        username.addEventListener("blur",function(){
            //如果用户名为空
            if(trim(this.value).length==0){
                feedback.innerHTML="用户名不得为空";
                errorMsg="用户名不得为空";
            }else{
                //如果用户名不为空，就执行ajax验证
                xhr.open("post","member.txt");
                xhr.send(null);
                xhr.addEventListener("readystatechange",function(){
                    if(xhr.readyState==4){
                        if(xhr.status==200){
                            if(trim(username.value)==xhr.responseText){
                                feedback.innerHTML="用户名已经存在";
                                errorMsg="用户名已经存在";
                            }else{
                                errorMsg="";
                            }
                            //console.log(xhr.responseText);
                        }
                    }
                })
                ///////////////
            }
        });
        /*用户名获得焦点时的验证*/
        username.addEventListener("focus",function(){
            feedback.innerHTML=errorMsg="";
        })
        /*检测邮箱格式*/
        email.addEventListener("keyup",function(){
            if(!valide_email(trim(this.value))){
                feedback.innerHTML="邮箱格式不正确";
                errorMsg="邮箱格式不正确";
                return false;
            }else{
                feedback.innerHTML="";
                errorMsg=false;
            }
        });
        /*点击提交按钮*/
        regBtn.addEventListener("click",function(){
            /*判断用户名不得为空*/
            if(trim(username.value).length==0){
                feedback.innerHTML="用户名不得为空";
                return false;
            }else{
                xhr.open("post","member.txt");
                xhr.send(null);
                xhr.addEventListener("readystatechange",function(){
                    if(xhr.readyState==4){
                        if(xhr.status==200){
                            if(trim(username.value)==xhr.responseText){
                                feedback.innerHTML="用户名已经存在";
                                errorMsg="用户名已经存在";
                            }else{
                                errorMsg="";
                            }
                            //console.log(xhr.responseText);
                        }
                    }
                })
            }
            /*密码不得为空*/
            if(trim(pwd.value).length==0){
                feedback.innerHTML="密码不得为空";
                return false;
            }else{
                if(valide_pwd(pwd.value)!=0){
                    feedback.innerHTML="密码强度不够";
                    return false;
                }else{
                    /*两次密码必须一致*/
                    if(trim(pwd.value)!=trim(repwd.value)){
                        feedback.innerHTML="两次密码不一致";
                        return false;
                    }
                    /**/
                    if(trim(email.value).length==0){
                        feedback.innerHTML="邮箱不得为空";
                        return false;
                    }
                }
            }
            /*验证不通过*/
            if(errorMsg){
                feedback.innerHTML=errorMsg;
                return false;
            }
            //alert(username.value);
            //把合法的用户名保存到sessionStorage中
            sessionStorage.setItem("username",username.value);
            location.href='login3.html';

        })
        ////禁止用户粘贴密码////////////
        repwd.addEventListener("paste",function(evt){
            evt.preventDefault();
        });













