<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>瀑布流布局</title>
    <style>
    *{padding:0;margin:0;}
        .clearfix:after,
.clearfix:before {
  content: " ";
  display: table;
}
.clearfix:after {
  clear: both;
}
.main {
  position: relative;
  -webkit-column-width: 210px;
  -moz-column-width: 210px;
  -webkit-column-gap: 5px;
  -moz-column-gap: 5px;
}
.box {
  float: left;
  padding: 15px 0 0 15px;
}
.box .pic {
  width: 180px;
  height: auto;
  padding: 10px;
  border-radius: 5px;
  box-shadow: 0 0 5px #cccccc;
  border: 1px solid #cccccc;
}
.box .pic img {
  display: block;
  width: 100%;
}

    </style>
</head>
<body>
    <div class="main clearfix" id="main">
        <div class="box">
            <div class="pic"><img src="./images/0.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/1.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/2.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/3.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/4.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/5.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/6.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/7.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/8.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/9.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/10.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/11.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/12.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/13.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/14.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/15.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/16.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/17.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/18.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/19.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/20.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/21.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/22.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/23.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/24.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/25.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/26.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/27.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/28.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/29.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/25.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/26.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/27.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/28.jpg"></div>
        </div>
        <div class="box">
            <div class="pic"><img src="./images/29.jpg"></div>
        </div>
    </div>
    <script>
window.onload = function(){
    waterfall('main','box');

    //模拟json数据
    var dataJson = {'data': [{'src':'30.jpg'},{'src':'31.jpg'},{'src':'32.jpg'},{'src':'33.jpg'},{'src':'34.jpg'},{'src':'35.jpg'},{'src':'36.jpg'},{'src':'37.jpg'},{'src':'38.jpg'},{'src':'39.jpg'},{'src':'40.jpg'},{'src':'41.jpg'},{'src':'42.jpg'},{'src':'43.jpg'},{'src':'44.jpg'},{'src':'45.jpg'}]};

    //监听scroll事件
    window.onscroll = function(){
        var isPosting = false;
        if(checkScollSlide('main','box') && !isPosting){
            var oParent = document.getElementById('main');
            for(var i in dataJson.data){
                isPosting = true;
                var oBox = document.createElement('div');
                oBox.className = 'box';
                oBox.innerHTML = '<div class="pic"><img src="./images/'+dataJson.data[i].src+'"></div>';
                oParent.appendChild(oBox);
            }
            isPosting = false;
            waterfall('main','box');
        }
    }

}

/*
* parent 父元素id clsName 块元素类*/
function waterfall(parent,clsName){
    //获取父元素
    var oParent = document.getElementById(parent),
    //获取所有box
    aBoxArr = oParent.getElementsByClassName(clsName),
    //单个box宽度
    iBoxW = aBoxArr[0].offsetWidth,
    // 列数
    cols = Math.floor(document.documentElement.clientWidth / iBoxW);

    oParent.style.cssText = 'width:'+iBoxW*cols+'px;margin:0 auto;';

    //储存所有的高度
    var hArr = [];
    for(var i = 0; i < aBoxArr.length; i++){
        if(i < cols){
            hArr[i] = aBoxArr[i].offsetHeight;
        }else{
            //获取hArr最小值
            var minH = Math.min.apply(null,hArr),
            // hArr最小值索引index
            minHIndex = getMinHIndex(hArr,minH);
            aBoxArr[i].style.cssText = 'position:absolute;top:'+minH+'px;left:'+aBoxArr[minHIndex].offsetLeft+'px;';

            //添加元素之后更新hArr
            hArr[minHIndex] += aBoxArr[i].offsetHeight;
        }
    }
}

//获取最小值索引
function getMinHIndex(arr,val){
    for(var i in arr){
        if(arr[i]  == val){
            return i;
        }
    }
}

//检查是否满足加载数据条件,parent 父元素id clsName 块元素类
function checkScollSlide(parent,clsName){
    var oParent = document.getElementById(parent),
        aBoxArr = oParent.getElementsByClassName(clsName),
        // 最后一个box元素的offsetTop+高度的一半
        lastBoxH = aBoxArr[aBoxArr.length - 1].offsetTop + aBoxArr[aBoxArr.length - 1].offsetHeight / 2,
        //兼容js标准模式和混杂模式
        scrollTop = document.documentElement.scrollTop || document.body.scrollTop,
        height = document.documentElement.clientHeight || document.body.clientHeight;
    return lastBoxH < scrollTop + height ? true : false;
}

</script>
    
</body>
</html>
