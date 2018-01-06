# echarts 使用
## 1.getStart
### 1.1引入 echart
```
  <!-- 引入 ECharts 文件 -->
    <script src="echarts.min.js"></script>
 ```
## 1.2异步调用
加载loading 动画
```
myChart.showLoading();
```
加载数据后隐藏loading
 ```
 myChart.hideLoading();
 ```
## 1.3动态数据
定时填入数据：
```
setInterval(function () {
    addData(true);
    myChart.setOption({
        xAxis: {
            data: date
        },
        series: [{
            name:'成交',
            data: data
        }]
    });
}, 500);

```
###1.4 图表中的交互
图例组件 legend、标题组件 title、视觉映射组件 visualMap、数据区域缩放组件 dataZoom、时间线组件 timeline

### 1.5代码触发 ECharts 中组件的行为
```
 setInterval(function () {
var dataLen = option.series[0].data.length;
// 取消之前高亮的图形
myChart2.dispatchAction({
type: 'downplay',
seriesIndex: 0,
dataIndex: app.currentIndex
});
app.currentIndex = (app.currentIndex + 1) % dataLen;
// 高亮当前图形
myChart2.dispatchAction({
type: 'highlight',
seriesIndex: 0,
dataIndex: app.currentIndex
});
// 显示 tooltip
myChart2.dispatchAction({
type: 'showTip',
seriesIndex: 0,
dataIndex: app.currentIndex
});
}, 1000);
```

### 1.6 使用svg
echart默认使用 canvas ,3.8以后可以使用svg渲染器；

```
// 使用 Canvas 渲染器（默认）
var chart = echarts.init(containerDom, null, {renderer: 'canvas'});
// 等价于：
var chart = echarts.init(containerDom);
// 使用 SVG 渲染器
var chart = echarts.init(containerDom, null, {renderer: 'svg'});
```
## 2.echart 方法
### 2.1 echarts 全局对象方法
1.init()
2.connect()
3.disconnect()
4.dispose()
5.getInstanceByDom()
6.registerMap();
7.getMap()
8.registerTheme();
9.graphic{ }

### 2.2 echartsInstance实例方法
![](img/1.png)

## 2.3 action 
![](img/2.png)

### 2.4 events
![](img/3.png)


n.其他问题 
n.1标签问题问
设置显示标签，并组织标签中的内容。
 label:{
  normal:{
      show: true,
       // 定义显示提示内容
      formatter: '{b}:{c}'
  }
}
n.2 使用百度作为底图
http://blog.csdn.net/yc_1993/article/details/52431989