<template>
    <!--设置背景图-->
    <div class="mybackground"></div>
    <!--页面主体-->
    <div class="screen_center">
        <h1 class="font_style">HOMEPAGE</h1>
    </div>
</template>

<script>
export default {
    name: 'HomePage',
}
</script>

<style scoped>
/*导入自定义字体*/
@import '../assets/css/font.css';

.font_style {
    /*字体样式*/
    font-family: XingKai, serif;
    /*字体粗细*/
    font-weight: 400;
    /*字体大小*/
    font-size: 120px;
    color: #bd3d0d;
}


.screen_center {
    position: fixed;
    top: 30%;
    left: 17%;
}

/*背景图设置*/
.mybackground {
    position: relative;
    background-image: url("../assets/data/bg1.jpg");
    width: 100%;
    height: 100vh;
    background-size: 100% 100%;
}

</style>