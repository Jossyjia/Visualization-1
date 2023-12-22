<template>
    <!--设置背景图-->
    <div class="mybackground"></div>
    <!--页面主体-->
    <div class="screen_center">
        <p class="font_style">哲学有三问：</p>
        <p class="font_style">我是谁？我从哪里来？我要到哪里去？</p>
        <p class="font_style">我们每时每刻或是在思考，或是在实践中寻找哲学三问的答案。而唯有铭记历史，立足过去，方能拾阶拿云，展望未来。</p>
    </div>
</template>

<script>
export default {
    name: 'ThanksPage',
}
</script>

<style scoped>
/*导入自定义字体*/
@import '../assets/css/font.css';

.font_style {
    /*字体样式*/
    font-family: Xiaoyao, serif;
    /*字体粗细*/
    font-weight: 400;
    /*字体大小*/
    font-size: 60px;
    color: #bd3d0d;
    
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
    background-image: url("../assets/data/bg13.png");    
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