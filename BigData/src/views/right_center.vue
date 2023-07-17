<!--
 * @Author: Johannjensen johannajensen1@gmail.com
 * @Date: 2023-07-15 20:35:43
 * @LastEditors: Johannjensen johannajensen1@gmail.com
 * @LastEditTime: 2023-07-17 09:54:48
 * @FilePath: \BigData\BigData\src\views\right_center.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->
<script setup>
import * as echarts from "echarts";
import { onMounted } from "vue";

onMounted(() => {
    rightcenter();
});

const rightcenter = () => {
    var chartDom = document.querySelector(".rightcenter");
    var myChart = echarts.init(chartDom);
    var option;

    // 背景图链接已删除
    // const piePatternImg = new Image();
    // piePatternImg.src = piePatternSrc;
    // const bgPatternImg = new Image();
    // bgPatternImg.src = bgPatternSrc;
    option = {
        // backgroundColor: 'white',
        // ,{
        //     // image: bgPatternImg,
        //     // repeat: "repeat",
        // },
        // 图表标题
        // title: {
        //     text: "饼图纹理",
        //     textStyle: {
        //         color: "#235894",
        //     },
        // },
        // tooltip: {
        //     top: '50%'
        // },
        series: [
            {
                name: "pie",
                type: "pie",
                selectedMode: "single",
                selectedOffset: 30,
                clockwise: true,
                top: "15%",
                // 饼图标题字体颜色
                label: {
                    fontSize: 18,
                    color: "#fff",
                },
                // 饼图线条颜色
                labelLine: {
                    lineStyle: {
                        color: "#fff",
                    },
                },
                data: [
                    { value: 1048, name: "Search Engine" },
                    { value: 735, name: "Direct" },
                    { value: 580, name: "Email" },
                    { value: 484, name: "Union Ads" },
                    { value: 300, name: "Video Ads" },
                ],
                // 背景图
                // itemStyle: {
                //     opacity: 0.7,
                //     color: {
                //         image: piePatternImg,
                //         repeat: "repeat",
                //     },
                //     borderWidth: 3,
                //     borderColor: "#235894",
                // },
            },
        ],
    };

    option && myChart.setOption(option);
};
</script>
<template>
    <div class="rightcenter"></div>
</template>
<style scoped>
.rightcenter {
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
