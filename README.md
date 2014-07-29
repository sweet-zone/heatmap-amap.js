heatmap-amap.js
===============

高德地图JS API V1.3的热力图实现，基于第三方库heatmap.js（官网地址：http://www.patrick-wied.at/static/heatmapjs/）。

##使用方法：

- 先后引入高德地图api和heatmap-amap.js

```html
  <script src="http://webapi.amap.com/maps?v=1.3&key=yourkey"></script>
  <script src="heatmap-amap.js"></script>
```
- 初始化高德热力图对象

```javascript
    /*
    * map：地图对象
    * opts：可选参数，其中
    *   radius：热力图每个点的半径
    *   visible：热力图是否显示
    *   opacity：热力图的透明度，取值范围0~100
    *   gradient：热力图的渐变区间
    * 可参考heatmap.js的文档：https://github.com/pa7/heatmap.js/blob/master/README.md
    */
    var config =  {
        radius: 30,
        visible: true,
        opacity: 40,
        gradient: { 0.45: 'rgb(0,0,255)', 0.55: 'rgb(0,255,255)', 0.65: 'rgb(0,255,0)', 0.95: 'yellow', 1.0: 'rgb(255,0,0)' }
    };
    var heatmap = new AMap.Heatmap(map, config);
```

- 调用start方法
  
```javascript
   heatmap.start();
```

- 设置数据。

```javascript
   var obj = {
        max: 90, //权重最大值
        //lng为精度值，lat为纬度值，count为权重
        data: [
            {lng:114.169922, lat:30.606004, count: 80},
            {lng:114.322357, lat:30.640275, count: 60},
            {lng:114.33197, lat:30.556348, count: 90},
            ...
        ]
    };

    //调用setDataSet()方法即可显示。
    heatmap.setDataSet(obj);
```

##API说明

heatmap-amap.js还暴露了一些方法。

- setDataSet，见使用方法
- addDataPoint(lng, lat, count)，添加一组数据显示在热力图中。
- toggle()，切换热力图的显示与隐藏。
- clear()，清除热力图。
