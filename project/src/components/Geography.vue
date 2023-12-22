DesignPage.vue
<template>
    <div class="mybackground"></div>
    <div class="main">
        <div class="title">
            <h1 class="font_style"> 中国博物馆分布图</h1>
            <p class="font_style2">
                中国博物馆发展显示显著区域差异。山东、北京、江苏、浙江等经济发达省份博物馆数量多、质量高、服务好，山东更是以623家博物馆领先全国。甘肃、陕西等GDP排名较低的省份也展现出博物馆发展的强势，彰显深厚的文化底蕴和政府支持。相较之下，海南、西藏、宁夏、青海等经济较弱地区的博物馆发展水平相对落后。这种分布反映了博物馆发展与经济实力、政府政策支持和地方文化底蕴的紧密联系。
            </p>
        </div>
        <div ref="GeographyComponent" class="Geography"></div>
        <div ref="sankeyContainer" class="sankeyContainer"></div>
    </div>
</template>

<script>
import * as echarts from 'echarts';
import chinaJson from '../data_json/china.json';
import provinceJson from '../data_json/sangji_province.json';

export default {
    name: 'DesignPage',
    methods: {
        initChart() {
            // 确保 DOM 元素可见且尺寸正确
            if (this.$refs.GeographyComponent.offsetWidth === 0 || this.$refs.GeographyComponent.offsetHeight === 0) {
                console.error('ECharts 初始化的 DOM 元素宽度或高度为零');
                return;
            }
            const Geography = echarts.init(this.$refs.GeographyComponent);
            echarts.registerMap('China', chinaJson);

            const option = {
                title: {
                    text: 'China Museum Statistics',
                    subtext: 'Example Data',
                    left: 'right'
                },
                tooltip: {
                    trigger: 'item',
                    showDelay: 0,
                    transitionDuration: 0.2
                },
                visualMap: {
                    left: 'right',
                    min: 0,
                    max: 700,
                    inRange: {
                        color: [
                            '#FFEFD5',
                            '#8B4513'
                        ]
                    },
                    text: ['High', 'Low'],
                    calculable: true
                },
                toolbox: {
                    show: true,
                    left: 'left',
                    top: 'top',
                    feature: {
                        dataView: { readOnly: false },
                        restore: {},
                        saveAsImage: {}
                    }
                },
                series: [
                    {
                        name: 'China Museum Statistics',
                        type: 'map',
                        map: 'China',
                        emphasis: { label: { show: true } },
                        data: [
                            { 'name': '北京市', 'value': 167 },
                            { 'name': '天津市', 'value': 69 },
                            { 'name': '河北省', 'value': 174 },
                            { 'name': '山西省', 'value': 197 },
                            { 'name': '内蒙古自治区', 'value': 173 },
                            { 'name': '辽宁省', 'value': 117 },
                            { 'name': '吉林省', 'value': 104 },
                            { 'name': '黑龙江省', 'value': 213 },
                            { 'name': '上海市', 'value': 128 },
                            { 'name': '江苏省', 'value': 335 },
                            { 'name': '浙江省', 'value': 420 },
                            { 'name': '安徽省', 'value': 234 },
                            { 'name': '福建省', 'value': 142 },
                            { 'name': '江西省', 'value': 179 },
                            { 'name': '山东省', 'value': 623 },
                            { 'name': '河南省', 'value': 384 },
                            { 'name': '湖北省', 'value': 234 },
                            { 'name': '湖南省', 'value': 174 },
                            { 'name': '广东省', 'value': 367 },
                            { 'name': '广西壮族自治区', 'value': 123 },
                            { 'name': '海南省', 'value': 37 },
                            { 'name': '重庆市', 'value': 121 },
                            { 'name': '四川省', 'value': 367 },
                            { 'name': '贵州省', 'value': 138 },
                            { 'name': '云南省', 'value': 169 },
                            { 'name': '西藏自治区', 'value': 12 },
                            { 'name': '陕西省', 'value': 323 },
                            { 'name': '甘肃省', 'value': 232 },
                            { 'name': '青海省', 'value': 41 },
                            { 'name': '宁夏回族自治区', 'value': 69 },
                            { 'name': '新疆维吾尔自治区', 'value': 101 }
                        ]
                    }
                ]
            };
            Geography.setOption(option);

            Geography.on('click', this.onMapClick);
        },
        onMapClick(params) {
            const provinceName = params.name;
            this.loadSankeyChart(provinceName);
            this.$refs.GeographyComponent.style.display = 'none';
            this.$refs.sankeyContainer.style.display = 'block';
        },
        loadSankeyChart(provinceName) {
            const data = provinceJson[provinceName];
            if (data) {
                this.createSankeyChart(this.$refs.sankeyContainer, data, provinceName);
            } else {
                console.log('No Sankey data found for province:', provinceName);
            }
        },
        createSankeyChart(container, data, provinceName) {
            // 清空容器内容
            // container.innerHTML = '';

            const sankeyChart = echarts.init(container);
            const option = {
                title: { text: '博物馆等级、类别与是否免费的桑基图：' + provinceName },
                tooltip: { trigger: 'item', triggerOn: 'mousemove' },
                series: [{
                    type: 'sankey',
                    layout: 'none',
                    color: ["#5a8f8f",
                        "#99a858",
                        "#f2c267"],

                    layoutIterations: 0,
                    data: data.nodes,
                    links: data.links,
                    emphasis: { focus: 'adjacency' },
                    lineStyle: { color: 'gradient', curveness: 0.5 }
                }]
            };
            sankeyChart.setOption(option);


            // 创建返回按钮，如果不存在
            if (!container.querySelector('#backButton')) {
                const backButton = document.createElement('button');
                backButton.id = 'backButton';
                backButton.innerText = '返回地图';
                backButton.style.position = 'absolute';
                backButton.style.top = '5px';
                backButton.style.right = '150px';
                backButton.addEventListener('click', () => {
                    this.$refs.GeographyComponent.style.display = 'block';
                    this.$refs.sankeyContainer.style.display = 'none';
                });

                container.appendChild(backButton);
            }
        }
    },
    mounted() {
        this.$nextTick(() => {
            this.initChart();
        });
    }
};
</script>
  
<!--scoped保证样式只影响当前页面-->
<style scoped>
@import '../assets/css/font.css';


/*图表样式*/
.Geography {
    /*图表宽度高度 用来设定图表展示出来的大小 一定要设置*/
    width: 1000px;
    height: 1400px;
    background-size: cover;
    margin-left: 400px;
    margin-top: -80px;
    margin-right: 0;
    /*margin-right: -10%;*/
    /*flex: 1;*/
    /*align-items: center;*/
}

.sankeyContainer {
    /*图表宽度高度 用来设定图表展示出来的大小 一定要设置*/
    width: 1000px;
    height: 800px;
    background-size: cover;
    margin-left: 500px;
    margin-top: 80px;
    margin-right: 0;
    /*margin-right: -10%;*/
    /*flex: 1;*/
    /*align-items: center;*/
}


/*标题样式*/
.title {
    position: fixed;
    top: 10%;
    margin-left: 1400px;
    margin-bottom: 20px;
    margin-top: 20px;
    width: 700px;
    /* 例如，设置宽度为 800 像素 */
    height: 600px;
    /* 例如，设置高度为 600 像素 */
}

.font_style2 {
    /* 字体样式 */
    font-family: 'Fengyun', serif;
    /* 假设 'Fengyun' 是您的字体名称 */
    /* 字体粗细 */
    font-weight: 40;
    /* 字体大小 */
    font-size: 25px;
    /* 文本颜色：非纯黑色 */
    color: #4a4a4a;
    /* 深灰色，更柔和的黑色 */
    /* 行高 */
    line-height: 1.5;
    /* 文本自动换行 */
    word-wrap: break-word;
    overflow-wrap: break-word;
    /* 边缘留白 */
    padding: 30px;
    /* 根据需要调整内边距 */
    margin: 30px;
    /* 根据需要调整外边距 */
}

.font_style {
    /*字体样式*/
    font-family: 'Fengyun', serif;
    /* 假设 'Fengyun' 是您的字体名称 */
    /* 字体粗细 */
    font-weight: 40;
    /* 字体大小 */
    font-size: 50px;
    /* 文本颜色：非纯黑色 */
    color: #4a4a4a;
    /* 深灰色，更柔和的黑色 */
    /* 行高 */
    line-height: 1.5;
    /* 文本自动换行 */
    word-wrap: break-word;
    overflow-wrap: break-word;
    /* 边缘留白 */
    padding: 30px;
    /* 根据需要调整内边距 */
    margin: 30px;
    /* 根据需要调整外边距 */
}

.main {
    z-index: 10;
    position: fixed;
    display: flex;
    flex-direction: row;
    width: 18400px;
    height: 100vh;
    left: 16600px;
    top: 0;
    /*align-items: center;*/
}

/*背景图设置*/
.mybackground {
    z-index: -1;
    position: relative;
    background-image: url("../assets/data/bg11.png");
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
    background-color: #fffcf7;
    /* 设置半透明背景色 */
    opacity: 0.5;
    /* 设置透明度，取值范围为0到1，1为完全不透明 */
}
</style>
  

  