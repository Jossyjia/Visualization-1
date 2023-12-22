<template>
    <!--设置背景图-->
    <div class="mybackground"></div>
    <!--页面主体-->
    <div class="screen_center">
        <h1 class="font_style">简介</h1>
        <p class="font_style2">商彝周鼎，什袭珍藏；吉光片羽，文脉华章。</p>
            <p class="font_style2">    泱泱华夏，滔滔长河；典籍珍宝，同垂不朽。</p>
        <p class="font_style2">本项目立足于故宫博物院、中国国家博物馆、敦煌莫高窟、青岛市内博物馆等馆藏文物数据，对其进行可视化分析，
            并基于此探讨文物背后的故事，继往开来，赓续文脉；同时借助技术分析结果思考文物遗产于今朝的意义，展现人文素养与家国情怀。</p>
    </div>
</template>

<script>
export default {
    name: 'IntroProject',
}
</script>

<style scoped>
/*导入自定义字体*/
@import '../assets/css/font.css';

.font_style2 {
    /*字体样式*/
    font-family: Xiaoyao, serif;
    /*字体粗细*/
    font-weight: 400;
    /*字体大小*/
    font-size: 50px;
    color: #c02b2b;
    line-height: 1.2;
    word-wrap: break-word;
    overflow-wrap: break-word;
}
.font_style {
    /*字体样式*/
    font-family: Xiaoyao, serif;
    /*字体粗细*/
    font-weight: 400;
    /*字体大小*/
    font-size: 50px;
    color: #c02b2b;
}

.screen_center {
    position: fixed;
    top: 10%;
    margin-left: 150px;
    margin-bottom: 20px; 
    width: 1400px; /* 例如，设置宽度为 800 像素 */
    height: 600px; /* 例如，设置高度为 600 像素 */
}

/*背景图设置*/
.mybackground {
    position: relative;
    background-image: url("../assets/data/bg2.png");
    width: 100%;
    height: 100vh;
    background-size: 100% 100%;
}
.mybackground::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: #fffcf7; /* 设置半透明背景色 */
    opacity: 0.5; /* 设置透明度，取值范围为0到1，1为完全不透明 */
}
</style>