DesignPage.vue
<template>
    <div class="mybackground"></div>
    <div class="main">
        <div id="ColorGraph" class="ColorGraphChart"></div>
        <div class="title">
            <h1 class="font_style">莫高窟颜色</h1>
            <p class="font_style2">
                中国古代流行所用的五种颜色是青、黄、赤、白、黑。古人从自然中观察万物，找到状态相对稳定的“固有色”，选择出与物相对应的这五种颜色，应用于绘画艺术中，形成中国最古老的色谱——五色谱。敦煌莫高窟艺术色彩运用也沿袭了古代“五色之变”的传统配色规律，作为其基本规律。

                李最雄在《敦煌莫高窟唐代绘画颜料分析研究》中说过：“唐代是我国古代封建历史上政治、经济、文化高度发达时期。”

                敦煌莫高窟在现存的492 个洞窟中，唐代壁画和彩塑占主导地位。艺术水平高、数量多、时间长，因此，可以把唐代称作敦煌莫高窟艺术史上的黄金时期。

                唐时期，不同阶段的色彩带给观者不同的审美感受。隋代壁画色彩细腻华丽、博采众长；初唐时期壁画色彩和谐细腻、自由洒脱；盛唐时期壁画色彩富丽华贵、气势恢宏；中唐时期壁画色彩趋向于清淡雅丽之感；晚唐时期壁画色彩单纯朴实，动情感人。
            </p>
        </div>
    </div>
</template>


<script>
export default {
    // 图表名称
    name: 'ColorGraph',
    methods: {
        myEcharts() {
            const ColorGraphChart = this.$echarts.init(document.getElementById('ColorGraph'));
            const option = {
                series: {
                    type: 'sankey',
                    layout: 'none',
                    emphasis: {
                        focus: 'adjacency'
                    },
                    layoutIterations: 0,
                    lineStyle: {
                        color: 'gradient',
                    },
                    data: [
                        { name: '初唐', itemStyle: { color: '#ed556a' }, },
                        { name: '盛唐', itemStyle: { color: '#de1c31' }, },
                        { name: '中唐', itemStyle: { color: '#f15642' }, },
                        { name: '晚唐', itemStyle: { color: '#862617' }, },
                        { name: '红色', itemStyle: { color: '#5a1216' }, },
                        { name: '蓝色', itemStyle: { color: '#134857' }, },
                        { name: '绿色', itemStyle: { color: '#223e36' }, },
                        { name: '棕黑色', itemStyle: { color: '#363433' }, },
                        { name: '白色', itemStyle: { color: '#fbecde' }, },
                        { name: '朱砂', itemStyle: { color: '#ff4c00' }, },
                        { name: '铅丹', itemStyle: { color: '#9d2933' }, },
                        { name: '土红', itemStyle: { color: '#873d24' }, },
                        { name: '角铅矿', itemStyle: { color: '#e57b58' }, },
                        { name: '石青', itemStyle: { color: '#2b333e' }, },
                        { name: '氯铜矿', itemStyle: { color: '#66c18c' }, },
                        { name: '石绿', itemStyle: { color: '#3de1ad' }, },
                        { name: '绿铜矿', itemStyle: { color: '#48c0a3' }, },
                        { name: '青金石', itemStyle: { color: '#a3d900' }, },
                        { name: '二氧化铅', itemStyle: { color: '#161823' }, },
                        { name: '方解石', itemStyle: { color: '#f0f0f4' }, },
                        { name: '石英', itemStyle: { color: '#f3f9f1' }, },
                        { name: '云母', itemStyle: { color: '#e9f1f6' }, },
                        { name: '滑石', itemStyle: { color: '#f0fcff' }, },
                        { name: '石膏', itemStyle: { color: '#e0f0e9' }, },
                    ],
                    links: [
                        { source: '初唐', target: '红色', value: 50 },
                        { source: '盛唐', target: '红色', value: 50 },
                        { source: '中唐', target: '红色', value: 50 },
                        { source: '晚唐', target: '红色', value: 50 },
                        { source: '初唐', target: '蓝色', value: 50 },
                        { source: '盛唐', target: '蓝色', value: 50 },
                        { source: '中唐', target: '蓝色', value: 50 },
                        { source: '晚唐', target: '蓝色', value: 50 },
                        { source: '初唐', target: '绿色', value: 50 },
                        { source: '盛唐', target: '绿色', value: 50 },
                        { source: '中唐', target: '绿色', value: 50 },
                        { source: '晚唐', target: '绿色', value: 50 },
                        { source: '初唐', target: '棕黑色', value: 50 },
                        { source: '盛唐', target: '棕黑色', value: 50 },
                        { source: '中唐', target: '棕黑色', value: 50 },
                        { source: '晚唐', target: '棕黑色', value: 50 },
                        { source: '初唐', target: '白色', value: 50 },
                        { source: '盛唐', target: '白色', value: 50 },
                        { source: '中唐', target: '白色', value: 50 },
                        { source: '晚唐', target: '白色', value: 50 },
                        { source: '红色', target: '朱砂', value: 80 },
                        { source: '红色', target: '铅丹', value: 60 },
                        { source: '红色', target: '土红', value: 60 },
                        { source: '蓝色', target: '石青', value: 80 },
                        { source: '蓝色', target: '氯铜矿', value: 50 },
                        { source: '蓝色', target: '石绿', value: 30 },
                        { source: '蓝色', target: '角铅矿', value: 10 },
                        { source: '蓝色', target: '青金石', value: 30 },
                        { source: '绿色', target: '石绿', value: 70 },
                        { source: '绿色', target: '石青', value: 70 },
                        { source: '绿色', target: '氯铜矿', value: 70 },
                        { source: '绿色', target: '绿铜矿', value: 60 },
                        { source: '棕黑色', target: '二氧化铅', value: 100 },
                        { source: '棕黑色', target: '铅丹', value: 100 },
                        { source: '白色', target: '方解石', value: 50 },
                        { source: '白色', target: '石英', value: 50 },
                        { source: '白色', target: '云母', value: 40 },
                        { source: '白色', target: '滑石', value: 50 },
                        { source: '白色', target: '方解石', value: 40 },
                    ]
                }
            };
            ColorGraphChart.setOption(option);
        }
    },
    mounted() {
        this.myEcharts();
    }
}
</script>

<!--scoped保证样式只影响当前页面-->
<style scoped>
@import '../assets/css/font.css';


/*图表样式*/
.ColorGraphChart {
    /*图表宽度高度 用来设定图表展示出来的大小 一定要设置*/
    width: 1000px;
    height: 900px;
    background-size: cover;
    margin-left: 400px;
    margin-top: 0;
    margin-right: 0;
    /*margin-right: -10%;*/
    /*flex: 1;*/
    /*align-items: center;*/
}

/*标题样式*/
.title {
    position: fixed;
    top: 10%;
    margin-left: 1300px;
    margin-bottom: 20px;
    width: 650px;
    color: #2a2828c7;
    /* 例如，设置宽度为 800 像素 */
    height: 600px;
    /* 例如，设置高度为 600 像素 */
}

.font_style2 {
    /*字体样式*/
    font-family: Fengyun, serif;
    /*字体粗细*/
    font-weight: 40;
    /*字体大小*/
    font-size: 30px;
    color: #2a2828c7;
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
    /* color: #c02b2b; */
}

.main {
    z-index: 11;
    position: fixed;
    display: flex;
    flex-direction: row;
    width: 2000px;
    height: 100vh;
    left: 11600px;
    top: 0;
    /*align-items: center;*/
}

/*背景图设置*/
.mybackground {
    z-index: -1;
    position: relative;
    background-image: url("../assets/data/bg4.png");
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
}</style>