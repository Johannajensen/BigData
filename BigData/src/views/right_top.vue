<!--
 * @Author: Johannjensen johannajensen1@gmail.com
 * @Date: 2023-07-15 20:23:33
 * @LastEditors: Johannjensen johannajensen1@gmail.com
 * @LastEditTime: 2023-07-15 20:51:27
 * @FilePath: \BigData\BigData\src\views\right_top.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<script setup>
import * as echarts from 'echarts';
import { onMounted } from 'vue';

onMounted(() => {
    righttop();
})
const righttop = () => {
    var chartDom = document.querySelector('.righttop');
    var myChart = echarts.init(chartDom);
    var option;

    option = {
        title: {
            text: '数据基本展示'
        },
        xAxis: {
            type: 'category',
            data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
        },
        yAxis: {
            type: 'value'
        },
        series: [
            {
                data: [120, 200, 150, 80, 70, 110, 130],
                type: 'bar',
                showBackground: true,
                backgroundStyle: {
                    color: 'rgba(180, 180, 180, 0.2)'
                }
            }
        ]
    };

    option && myChart.setOption(option);

}
</script>
<template>
    <div class="righttop">

    </div>
</template>

<style scoped>
.righttop {
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
}
</style>