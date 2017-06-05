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
 
