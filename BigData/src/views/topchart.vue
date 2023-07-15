<!--
 * @Author: Johannjensen johannajensen1@gmail.com
 * @Date: 2023-07-15 10:59:45
 * @LastEditors: Johannjensen johannajensen1@gmail.com
 * @LastEditTime: 2023-07-15 17:15:58
 * @FilePath: \BigData\BigData\src\views\topchart.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<script setup>
import * as echarts from 'echarts';

import { onMounted } from 'vue';

onMounted(() => {
    echarts_top();
})


const echarts_top = () => {
    var app = {};
    var chartDom = document.getElementById('top');
    var myChart = echarts.init(chartDom);
    var option;


    const categories = (function () {
        let now = new Date();
        let res = [];
        let len = 10;
        while (len--) {
            res.unshift(now.toLocaleTimeString().replace(/^\D*/, ''));
            now = new Date(+now - 2000);
        }
        return res;
    })();
    const categories2 = (function () {
        let res = [];
        let len = 10;
        while (len--) {
            res.push(10 - len - 1);
        }
        return res;
    })();
    const data = (function () {
        let res = [];
        let len = 10;
        while (len--) {
            res.push(Math.round(Math.random() * 1000));
        }
        return res;
    })();
    const data2 = (function () {
        let res = [];
        let len = 0;
        while (len < 10) {
            res.push(+(Math.random() * 10 + 5).toFixed(1));
            len++;
        }
        return res;
    })();
    option = {
        tooltip: {
            trigger: 'axis',
            axisPointer: {
                type: 'cross',
                label: {
                    backgroundColor: '#283b56'
                }
            }
        },
        legend: {},
        toolbox: {
            show: true,
            feature: {
                dataView: { readOnly: false },
                restore: {},
                saveAsImage: {}
            }
        },
        dataZoom: {
            show: false,
            start: 0,
            end: 100
        },
        xAxis: [
            {
                type: 'category',
                boundaryGap: true,
                data: categories,
                // axisLabel: { //轴文字标签
                //     show: true,
                //     textStyle: {
                //         color: '#B0CEFC',
                //     }
                // },
                nameTextStyle: {
                    color: '#fff'
                }
            },
            {
                type: 'category',
                boundaryGap: true,
                data: categories2,
                // axisLabel: { //轴文字标签
                //     show: true,
                //     textStyle: {
                //         color: '#B0CEFC',
                //     }
                // },
                nameTextStyle: {
                    color: '#fff'
                }
            },


        ],
        yAxis: [
            {
                type: 'value',
                scale: true,
                name: '价格',
                max: 30,
                min: 0,
                boundaryGap: [0.2, 0.2],
                nameTextStyle: {
                    color: '#fff'
                }
            },
            {
                type: 'value',
                scale: true,
                name: '指数',
                max: 1200,
                min: 0,
                boundaryGap: [0.2, 0.2],
                nameTextStyle: {
                    color: '#fff'
                }
            }
        ],
        series: [
            {
                name: '主要内容展示区',
                type: 'bar',
                xAxisIndex: 1,
                yAxisIndex: 1,
                data: data,
                top: '35%',
            },
            {
                name: '次要内容展示区',
                type: 'line',
                data: data2,
                top: '35%',
                nameTextStyle: {
                    color: '#fff'
                }
            }
        ]
    };
    app.count = 11;
    setInterval(function () {
        let axisData = new Date().toLocaleTimeString().replace(/^\D*/, '');
        data.shift();
        data.push(Math.round(Math.random() * 1000));
        data2.shift();
        data2.push(+(Math.random() * 10 + 5).toFixed(1));
        categories.shift();
        categories.push(axisData);
        categories2.shift();
        categories2.push(app.count++);
        myChart.setOption({
            xAxis: [
                {
                    data: categories
                },
                {
                    data: categories2
                }
            ],
            series: [
                {
                    data: data
                },
                {
                    data: data2
                }
            ]
        });
    }, 2100);

    option && myChart.setOption(option);
}

</script>

<template>
    <div id="top"></div>
</template>
<style scoped>
#top {
    background-image: url(images/line.png);
    background-size: cover;
    width: 100%;
    height: 100%;
    padding-top: 10px;
    /* background-color: rgba(72, 71, 71, 0.591); */
    border: 1px solid rgba(25, 186, 139, .17);
    border-radius: 30px;
    color: #fff
}

;
</style>