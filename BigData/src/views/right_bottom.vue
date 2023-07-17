<!--
 * @Author: Johannjensen johannajensen1@gmail.com
 * @Date: 2023-07-15 20:43:00
 * @LastEditors: Johannjensen johannajensen1@gmail.com
 * @LastEditTime: 2023-07-17 10:12:33
 * @FilePath: \BigData\BigData\src\views\right_bottom.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<script setup>
import * as echarts from 'echarts';
import { onMounted } from 'vue';


onMounted(() => {
    rightbottom();
})
const rightbottom = () => {
    var chartDom = document.querySelector('.rightbottom');
    var myChart = echarts.init(chartDom);
    var option;

    option = {
        // title: [
        //     {
        //         text: 'Tangential Polar Bar Label Position (middle)'
        //     }
        // ],
        polar: {
            radius: [30, '80%']
        },
        textStyle: {
            color:'white'
        },
        angleAxis: {
            max: 4,
            startAngle: 75
        },
        radiusAxis: {
            type: 'category',
            data: ['a', 'b', 'c', 'd']
        },
        tooltip: {},
        series: {
            type: 'bar',
            data: [2, 1.2, 2.4, 3.6],
            coordinateSystem: 'polar',
            label: {
                show: true,
                position: 'middle',
                formatter: '{b}: {c}'
            }
        }
    }

    option && myChart.setOption(option);
};

</script>
<template>
    <div class="rightbottom"></div>
</template>

<style scoped>
.rightbottom {
    background-image: url(images/line.png);
    background-size: cover;
    width: 100%;
    height: 100%;
    padding-top: 10px;
    background-color: rgba(255, 255, 255, .04);
    border: 1px solid rgba(25, 186, 139, .17);
    border-radius: 30px;
    color: white;
    padding: 10px;
    overflow: hidden;
}
</style>