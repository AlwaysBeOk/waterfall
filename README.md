<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>�ٲ�������</title>
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

    //ģ��json����
    var dataJson = {'data': [{'src':'30.jpg'},{'src':'31.jpg'},{'src':'32.jpg'},{'src':'33.jpg'},{'src':'34.jpg'},{'src':'35.jpg'},{'src':'36.jpg'},{'src':'37.jpg'},{'src':'38.jpg'},{'src':'39.jpg'},{'src':'40.jpg'},{'src':'41.jpg'},{'src':'42.jpg'},{'src':'43.jpg'},{'src':'44.jpg'},{'src':'45.jpg'}]};

    //����scroll�¼�
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
* parent ��Ԫ��id clsName ��Ԫ����*/
function waterfall(parent,clsName){
    //��ȡ��Ԫ��
    var oParent = document.getElementById(parent),
    //��ȡ����box
    aBoxArr = oParent.getElementsByClassName(clsName),
    //����box���
    iBoxW = aBoxArr[0].offsetWidth,
    // ����
    cols = Math.floor(document.documentElement.clientWidth / iBoxW);

    oParent.style.cssText = 'width:'+iBoxW*cols+'px;margin:0 auto;';

    //�������еĸ߶�
    var hArr = [];
    for(var i = 0; i < aBoxArr.length; i++){
        if(i < cols){
            hArr[i] = aBoxArr[i].offsetHeight;
        }else{
            //��ȡhArr��Сֵ
            var minH = Math.min.apply(null,hArr),
            // hArr��Сֵ����index
            minHIndex = getMinHIndex(hArr,minH);
            aBoxArr[i].style.cssText = 'position:absolute;top:'+minH+'px;left:'+aBoxArr[minHIndex].offsetLeft+'px;';

            //���Ԫ��֮�����hArr
            hArr[minHIndex] += aBoxArr[i].offsetHeight;
        }
    }
}

//��ȡ��Сֵ����
function getMinHIndex(arr,val){
    for(var i in arr){
        if(arr[i]  == val){
            return i;
        }
    }
}

//����Ƿ����������������,parent ��Ԫ��id clsName ��Ԫ����
function checkScollSlide(parent,clsName){
    var oParent = document.getElementById(parent),
        aBoxArr = oParent.getElementsByClassName(clsName),
        // ���һ��boxԪ�ص�offsetTop+�߶ȵ�һ��
        lastBoxH = aBoxArr[aBoxArr.length - 1].offsetTop + aBoxArr[aBoxArr.length - 1].offsetHeight / 2,
        //����js��׼ģʽ�ͻ���ģʽ
        scrollTop = document.documentElement.scrollTop || document.body.scrollTop,
        height = document.documentElement.clientHeight || document.body.clientHeight;
    return lastBoxH < scrollTop + height ? true : false;
}

</script>
    
</body>
</html>
