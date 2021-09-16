<template>
  <div class="homepage">
    <h1 id='welcome'>Welcome</h1>
    <h2 id='time' style="color:rgb(59 165 118);">clock</h2>
  </div>
</template>

<script>
    export default {
      name: "Yeqi"
    }

    //等待页面加载完执行
    window.onload=function(){
      var T = document.getElementById('welcome');			//通过id获取div节点对象
      console.log(T);
      T.innerHTML = "Welcome to yeqi's HomePage";		//在div中追加内容222222
      //document.write("<h4>Hello World!<br>Have a nice <b>加班</b> day!</h4>");
      console.log("hello")
      refreshTime();		//当页面加载完时运行时间函数
      //PayOff();
    }

    //   文字时钟
    function checkTime(i){
      if(i<10){
        i='0'+i//定义当分钟，秒钟小于10时，使一位数显示为两位数
      }
      return i//大于10时，正常显示
    }

    function refreshTime(){                               //定义时间函数
      var date=new Date();                                //获取当前默认格式的当前时间
      var myYear=date.getFullYear();                      //在默认格式时间中提取四位数的年份
      var myMonth=date.getMonth()+1;                      //在默认格式时间中提取月份，（月份返回值是0-11，实际月份要返回值+1）
      var myDate=date.getDate();                          //在默认格式实践中提取日期
      var myDay=date.getDay();                            //在默认格式中提取星期（返回值0-6对应星期天-星期六）
      var week=['星期天','星期一','星期二','星期三','星期四','星期五','星期六',]//创建数组对应myDay
      var myHours=date.getHours();                        //在默认格式实践中提取日期小时
      var myMinutes=date.getMinutes();                    //在默认格式实践中提取日期分钟
      var mySeconds=date.getSeconds();                    //在默认格式实践中提取日期分钟
      var pushM=checkTime(myMinutes);
      var pushS=checkTime(mySeconds);                     //用checkTime函数使时间为0~9时替换为00~09
      //alert(myDay);//test
      document.getElementById('time').innerHTML=myYear+'年'+myMonth+'月'+myDate+'日&nbsp&nbsp'+week[myDay]+'&nbsp&nbsp'+myHours+':'+pushM+':'+pushS+'<br/>'//使id为'time'的文本值替换为该格式的时间
      setTimeout(refreshTime,1000);               //每1000毫秒运行一次refreshTime函数，即每秒刷新一次时间
    }

</script>

<style scoped>
#homepage {
  background-color: #000000;
}
</style>
