<!--
 * @Author: Johannjensen johannajensen1@gmail.com
 * @Date: 2023-07-15 14:53:03
 * @LastEditors: Johannjensen johannajensen1@gmail.com
 * @LastEditTime: 2023-07-15 22:23:43
 * @FilePath: \BigData\BigData\src\views\middel_map.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<script setup>
import * as echarts from 'echarts';
import { onMounted, ref } from 'vue';
import china from '../../China.json'

onMounted(() => {
  map();
})
// 散点图数据
const points = ref([
  { name: '新疆', value: [87.628579, 43.793301], itemStyle: { color: '#00EEFF' } }, // 新疆
  { name: '四川', value: [104.076452, 30.651696], itemStyle: { color: '#00EEFF' } }, // 四川
  { name: '甘肃', value: [103.826777, 36.060634], itemStyle: { color: '#00EEFF' } }, // 甘肃
  { name: '云南', value: [102.709372, 25.046432], itemStyle: { color: '#00EEFF' } }, // 云南
  { name: '广西', value: [108.327537, 22.816659], itemStyle: { color: '#00EEFF' } }, // 广西
  { name: '湖南', value: [112.982951, 28.116007], itemStyle: { color: '#00EEFF' } }, // 湖南
  { name: '山东', value: [117.020725, 36.670201], itemStyle: { color: '#00EEFF' } }, // 山东
  { name: '河南', value: [113.753094, 34.767052], itemStyle: { color: '#00EEFF' } }, // 河南
  { name: '山西', value: [112.578781, 37.813948], itemStyle: { color: '#00EEFF' } }, // 山西
  { name: '福建', value: [119.296194, 26.101082], itemStyle: { color: '#00EEFF' } }, // 福建
  { name: '浙江', value: [120.152575, 30.266619], itemStyle: { color: '#00EEFF' } }, // 浙江
  { name: '江苏', value: [118.763563, 32.061377], itemStyle: { color: '#00EEFF' } }, // 江苏
  { name: '北京', value: [116.407387, 39.904179], itemStyle: { color: '#A6283F' } }, // 北京
  { name: '陕西', value: [108.953939, 34.266611], itemStyle: { color: '#00EEFF' } }, // 陕西
  { name: '广东', value: [113.266887, 23.133306], itemStyle: { color: '#00EEFF' } } // 广东
])

const lineData = ref([
  { coords: [[113.753094, 34.767052], [87.628579, 43.793301]] },// 河南->新疆
  { coords: [[113.753094, 34.767052], [104.076452, 30.651696]] },// 河南->四川
  { coords: [[113.753094, 34.767052], [103.826777, 36.060634]] },// 河南->甘肃
  { coords: [[113.753094, 34.767052], [102.709372, 25.046432]] },// 河南->云南
  { coords: [[113.753094, 34.767052], [108.327537, 22.816659]] },// 河南->广西
  { coords: [[113.753094, 34.767052], [112.982951, 28.116007]] },// 河南->湖南
  { coords: [[113.753094, 34.767052], [117.020725, 36.670201]] },// 河南->山东
  { coords: [[113.753094, 34.767052], [113.753094, 34.767052]] },// 河南->河南
  { coords: [[113.753094, 34.767052], [112.578781, 37.813948]] },// 河南->山西
  { coords: [[113.753094, 34.767052], [119.296194, 26.101082]] },// 河南->福建
  { coords: [[113.753094, 34.767052], [120.152575, 30.266619]] },// 河南->浙江
  { coords: [[113.753094, 34.767052], [118.763563, 32.061377]] },// 河南->安徽
  { coords: [[113.753094, 34.767052], [113.266887, 23.133306]] },// 河南->广东
  { coords: [[113.753094, 34.767052], [108.953939, 34.266611]] }// 河南->陕西
])

const map = () => {
  var chartDom = document.getElementById('map');
  var myChart = echarts.init(chartDom);
  var option;
  option = {
    // backgroundColor: '#0E2152',// 背景颜色
    geo: {// 地图配置
      map: 'china',
      label: { // 图形上的文本标签
        normal: {// 通常状态下的样式
          show: true,
          textStyle: {
            color: '#fff'
          }
        },
        emphasis: {// 鼠标放上去高亮的样式
          textStyle: {
            color: '#fff'
          }
        }
      },
      itemStyle: {// 地图区域的样式设置
        normal: { // 通常状态下的样式
          borderColor: '#5089EC',
          borderWidth: 1,
          areaColor: { //地图区域的颜色
            type: 'radial', // 径向渐变
            x: 0.5, // 圆心
            y: 0.5,// 圆心
            r: 0.8,// 半径
            colorStops: [
              { // 0% 处的颜色
                offset: 0,
                color: 'rgba(0, 102, 154, 0)'
              },
              { // 100% 处的颜色
                offset: 1,
                color: 'rgba(0, 102, 154, .4)'
              }
            ]
          }
        },
        // 鼠标放上去高亮的样式
        emphasis: {
          areaColor: '#2386AD',
          borderWidth: 0
        }
      }
    },
    series: [
      { // 散点系列数据
        type: 'effectScatter',// 带有涟漪特效动画的散点（气泡）图
        coordinateSystem: 'geo', //该系列使用的坐标系:地理坐标系
        // 特效类型,目前只支持涟漪特效'ripple'，意为“涟漪”
        effectType: 'emphasis',
        // 配置何时显示特效。可选'render'和'emphasis' 。
        showEffectOn: 'render',
        rippleEffect: { // 涟漪特效相关配置。
          period: 10, // 动画的周期，秒数。
          scale: 2,// 动画中波纹的最大缩放比例。
          // 波纹的绘制方式，可选 'stroke' 和 'fill'。
          brushType: 'stroke'
        },
        zlevel: 1, // 所有图形的 zlevel 值。
        data: points.value
      },
      { // 线条系列数据
        type: 'lines',
        zlevel: 2,
        symbol: ['none', 'arrow'], // 标记的图形: 箭头
        symbolSize: 10, // 标记的大小
        effect: { // 线条特效的配置
          show: true,
          period: 6, // 特效动画的时间，单位s
          trailLength: 0, // 特效尾迹的长度。取值[0,1]值越大，尾迹越重
          // 特效图形的标记 可选'circle'等
          symbolSize: 15// 特效标记的大小
        },
        lineStyle: { // 线条样式
          normal: {
            color: '#93EBF8',
            width: 1.0, // 线条宽度
            opacity: 0.6, // 尾迹线条透明度
            curveness: 0.2// 尾迹线条曲直度
          }
        },
        data: lineData.value
      }
    ]
  }
  // 地图注册，第一个参数的名字必须和option.geo.map一致
  echarts.registerMap('china', china)
  myChart.setOption(option)
}


</script>

<template>
  <div id="map"></div>
</template>
<style scoped>
#map{
  width: 100%;
  height: 100%;
  overflow: hidden;
}
</style>