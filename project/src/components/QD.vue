DesignPage.vue
<template>
    <div class="mybackground"></div>
    <div class="main">
        <div class="background">
            <button class="button1" @click="showImage('sddx.png', { top: '50', left: '860' },'山东大学百余年历程波澜起伏，足令人感怀壮情；\n孰不知，这其中还汇聚着早期博物馆的沧桑与斑驳，\n博物馆的特殊作用在山大历史上留下了深刻的印迹。\n山东大学深厚的文化底蕴已浑化成一股强劲的撑力，\n撑点越高，我们就跃得更高。',{top: '480px', left: '850px'})">
                按钮1
            </button>
            <button class="button2" @click="showImage('hj.png', { top: '50', left: '860' },'中国人民解放军海军博物馆\n是中国唯一一座反映中国海军发展的军事博物馆.\n是人民海军的历史高地、精神高地、文化高地。\n海军博物馆围绕传承红色基因、牢记初心使命，\n着力建成国内领先、世界一流的海军博物馆。',{top: '480px', left: '850px'})">
                按钮2
            </button>
            <button class="button3" @click="showImage('qd.png', { top: '50', left: '860' },'青岛市博物馆，\n坐落于青岛这片历史悠久而充满活力的城市，\n其百余年的历程同样见证了青岛的发展和变迁。\n青岛市博物馆是历史的守护者，是传播文化的平台。\n为人民提供了一个深入了解本地历史、文化的机会，\n为社会的进步和发展贡献着自己的力量。',{top: '480px', left: '850px'})">
                按钮3
            </button>
            <button class="button4" @click="showImage('a.png', { top: '30', left: '860' },'青岛市位于中国东海岸，是充满着文化底蕴的城市。\n青岛以其深厚的历史传承和独特的文化景观而闻名。\n青岛拥有两座国家一级、三座国家二级博物馆，\n各种珍贵的展品向人们展示了青岛的深厚底蕴。\n这些博物馆是历史的见证者，是文化传承的宝库。',{top: '480px', left: '850px'})">
                主按钮
            </button>
            <button class="button5" @click="showImage('pj.png', { top: '50', left: '860' },'青岛啤酒博物馆共分为三个展区\n打造历史文化、酿造工艺、啤酒魅力的神秘之旅。\n吸引了100多个国家和地区的中外宾客纷至沓来，\n自开馆以来累计接待游客超过一千万人次。',{top: '480px', left: '850px'})">
                按钮5
            </button>
            <button class="button6" @click="showImage('yz.png', { top: '50', left: '860' },'青岛一战遗址博物馆全面展现一战对中国命运影响\n整个建筑造型像一只展翅飞翔的鸽子,寓意珍爱和平。\n“还我青岛”的对外抗争成为民族意识觉醒的起点，\n“五四运动”揭开了反帝反封建运动的新篇章。\n',{top: '480px', left: '850px'})">
                按钮6
            </button>
            <div id="imageContainer"></div>
        </div>
    </div>
</template>


<script>
function fadeIn(element) {
    element.style.opacity = 0;
    let opacity = 0;
    const intervalId = setInterval(function() {
        if (opacity < 1) {
            opacity += 0.1; // 调整透明度增加的速度
            element.style.opacity = opacity;
        } else {
            clearInterval(intervalId);
        }
    }, 100); // 调整每次增加透明度的间隔时间
}
export default {
    name: 'QDGraph',
    methods: {
        showImage(imageSrc, position, textContent = '默认文是啥本', textPosition = {top: '20px', left: '0px'}) {
    const imageContainer = document.getElementById('imageContainer');
    const img = document.createElement('img');
    img.src = imageSrc;
    img.alt = '图片';
    img.style.position = 'absolute';
     img.style.top = position.top+'px' ;
     img.style.left = position.left+'px' ;
    img.style.opacity = '0';
    const text = document.createElement('p');
    text.textContent = textContent;
    text.style.whiteSpace = 'pre-line';
    text.style.position = 'absolute';
    text.style.top = textPosition.top;
    text.style.left = textPosition.left;
    text.style.color = 'rgba(2, 3, 9, 0.6)';
    text.style.fontSize = '40px';
    text.style.opacity = '0';
    text.style.fontFamily ="Fengyun, serif";
    setTimeout(function () {
        img.style.opacity = '1';
        text.style.opacity = '1';
    }, 500);

    imageContainer.innerHTML = '';
    fadeIn(img);
    fadeIn(text);
    imageContainer.appendChild(img);
    imageContainer.appendChild(text);
    
}

    },
}
</script>

<!--scoped保证样式只影响当前页面-->
<style scoped>
@import '../assets/css/font.css';

img {
    position: fixed;
    width: 400px;
    background-size: cover;
    height: 400px;
    display: block;
    top:15px;
}

.background {
    width: 800px;
    height: 800px;
    background-image: url('../assets/data/map.png');
    background-size: cover;
}


.button1 {
    display: block;
    margin-bottom: 10px;
    position: absolute;
    z-index: 2;
    opacity: 0.7;
    width: 40px; /* Adjust the width of the button */
    height: 40px; /* Adjust the height of the button */
    border-radius: 50%; /* Make the button circular */
    margin-top: 100px;
    margin-left: 130px;
}

.button2 {
    display: block;
    margin-bottom: 10px;
    position: absolute;
    z-index: 2;
    opacity: 0.7;
    width: 40px; /* Adjust the width of the button */
    height: 40px; /* Adjust the height of the button */
    border-radius: 50%; /* Make the button circular */
    margin-top: 200px;
    margin-left: 130px;
}

.button3 {
    display: block;
    margin-bottom: 10px;
    position: absolute;
    z-index: 2;
    opacity: 0.7;
    width: 40px; /* Adjust the width of the button */
    height: 40px; /* Adjust the height of the button */
    border-radius: 50%; /* Make the button circular */
    margin-top: 300px;
    margin-left: 130px;
}

.button4 {
    display: block;
    margin-bottom: 30px;
    position: absolute;
    z-index: 2;
    opacity: 0.7;
    width: 80px; /* Adjust the width of the button */
    height: 80px; /* Adjust the height of the button */
    border-radius: 50%; /* Make the button circular */
    margin-top: 400px;
    margin-left: 130px;
}

.button5 {

    display: block;
    margin-bottom: 10px;
    position: absolute;
    z-index: 2;
    opacity: 0.7;
    width: 40px; /* Adjust the width of the button */
    height: 40px; /* Adjust the height of the button */
    border-radius: 50%; /* Make the button circular */
    margin-top: 500px;
    margin-left: 130px;
}

.button6 {
    display: block;
    margin-bottom: 10px;
    position: absolute;
    z-index: 2;
    opacity: 0.7;
    width: 40px; /* Adjust the width of the button */
    height: 40px; /* Adjust the height of the button */
    border-radius: 50%; /* Make the button circular */
    margin-top: 600px;
    margin-left: 130px;
}


/*标题样式*/
.title {
    /*字体样式*/
    font-family: XingKai, serif;
    /*字体粗细*/
    font-weight: 40;
    /*字体大小*/
    font-size: 50px;
    color: rgba(2, 3, 9, 0.6);
    flex: 1;
    width: 100px;
    height: 100px;
    margin-top: 100px;
    margin-left: 100px;
    z-index: 1;
}


.main {
    z-index: 10;
    position: fixed;
    display: flex;
    flex-direction: row;
    width: 15500px;
    height: 100vh;
    left: 13500px;
    top: 0;
    /*align-items: center;*/
}

/*背景图设置*/
.mybackground {
    z-index: -1;
    position: relative;
    background-image: url("../assets/data/bg9.png");
    width: 100%;
    min-height: 100vh;
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