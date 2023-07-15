<!--
 * @Author: Johannjensen johannajensen1@gmail.com
 * @Date: 2023-07-15 10:22:23
 * @LastEditors: Johannjensen johannajensen1@gmail.com
 * @LastEditTime: 2023-07-15 20:50:05
 * @FilePath: \BigData\BigData\src\components\index.vue
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AEigh
-->
<script setup>
import topchart from '../views/topchart.vue';
import mainchart from '../views/mainchart.vue';
import Bottomchart from '../views/bottomchart.vue';
import Middel_map from '../views/middel_map.vue';
import Right_top from '../views/right_top.vue';
import Right_center from '../views/right_center.vue';
import Right_bottom from '../views/right_bottom.vue';

</script>

<template>
    <header>
        <h1>数据可视化监控大屏</h1>
    </header>
    <main>
        <div class="left">
            <div class="top">
                <topchart />
            </div>
            <div class="center">
                <mainchart />
            </div>
            <div class="bottom">
                <Bottomchart />
            </div>
        </div>
        <div class="middle">
            <Middel_map />
        </div>
        <div class="right">
            <div class="right_top">
                <Right_top />
            </div>
            <div class="right_center">
                <Right_center />
            </div>
            <div class="right_bottom">
                <Right_bottom />
            </div>
        </div>
    </main>
</template>

<style scoped>
header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    background-image: url(images/head_bg.png);
    background-size: cover;
    color: white;
    height: 70px;
}

main {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    height: 100%;
}

.left {
    /* background-color: aquamarine; */
    height: 100%;
    width: 400px;
    display: flex;
    flex-direction: column;

}

.left .top {
    height: 400px;


}

.left .center {
    height: 300px;
    margin: 18px 0;

}

.left .bottom {
    height: 400px;


}

.middle {
    flex: 1;
    background-color: rgba(87, 87, 175, 0.454);
}

.right {
    /* background-color: aquamarine; */
    height: 100%;
    width: 480px;
    display: flex;
    flex-direction: column;
}

.right .right_top {
    width: 100%;
    height: 300px;
    /* background-color: rgb(24, 43, 37); */
}

.right_center {
    flex: 1;
    /* background-color: bisque; */
    margin: 18px 0;
}

.right_bottom {
    height: 300px;
    width: 100%;
    background-color: blanchedalmond;

}
</style>