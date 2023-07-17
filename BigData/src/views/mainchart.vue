<!--
 * @Author: Johannjensen johannajensen1@gmail.com
 * @Date: 2023-07-15 11:16:30
 * @LastEditors: Johannjensen johannajensen1@gmail.com
 * @LastEditTime: 2023-07-17 09:34:16
 * @FilePath: \BigData\BigData\src\views\mainchart.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<script setup>
import * as echarts from 'echarts';
import { onMounted } from 'vue';

onMounted(() => {
    center_chart();
})

const center_chart = () => {
    var chartDom = document.getElementById('center');
    var myChart = echarts.init(chartDom);
    var option;

    const data = [];
    for (let i = 0; i < 5; ++i) {
        data.push(Math.round(Math.random() * 200));
    }
    option = {
        tooltip: {
            trigger: 'item'
        },
        legend: {
            top: '18%',
        },
        xAxis: {
            max: 'dataMax'
        },
        yAxis: {
            type: 'category',
            data: ['A', 'B', 'C', 'D', 'E'],
            inverse: true,
            animationDuration: 300,
            animationDurationUpdate: 300,
            max: 3 // only the largest 3 bars will be displayed
        },
        textStyle: {
            color: 'white'
        },
        series: [
            {
                realtimeSort: true,
                name: '基础数据展示',
                type: 'bar',
                data: data,
                label: {
                    show: true,
                    position: 'right',
                    valueAnimation: true,
                },
                top: '35%'
            }
        ],
        legend: {
            show: true,
            data: [{
                name: '基础数据展示',
                textStyle: { color: 'white' }
            }]
        },
        animationDuration: 0,
        animationDurationUpdate: 3000,
        animationEasing: 'linear',
        animationEasingUpdate: 'linear'
    };
    function run() {
        for (var i = 0; i < data.length; ++i) {
            if (Math.random() > 0.9) {
                data[i] += Math.round(Math.random() * 2000);
            } else {
                data[i] += Math.round(Math.random() * 200);
            }
        }
        myChart.setOption({
            series: [
                {
                    type: 'bar',
                    data,
                }
            ]
        });
    }
    setTimeout(function () {
        run();
    }, 0);
    setInterval(function () {
        run();
    }, 3000);

    option && myChart.setOption(option);
}
</script>

<template >
    <div id="center">

    </div>
</template>
<style scoped>
#center {
    background-image: url(images/line.png);
    background-size: cover;
    width: 100%;
    height: 100%;
    padding-top: 10px;
    background-color: rgba(255, 255, 255, .04);
    border: 1px solid rgba(25, 186, 139, .17);
    border-radius: 30px;
    color: white;
}
</style>