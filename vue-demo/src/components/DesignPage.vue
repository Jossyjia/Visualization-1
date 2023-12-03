<template>
    <div class="mybackground"></div>
    <div class="main">
        <!--这里通过下面这行代码进行绘图 通过BarChartId进行指定-->
        <div id="BarChartId" class="Chart"></div>
        <!--标题-->
        <div class="title">
            <h1>地理数据</h1>
        </div>
        <!--主体文字内容-->
        <div class="content">
            <p>中国存在很多的名胜古迹，古代的诗人常常游历山川，借名胜古迹中抒发自己的情感，通过对唐宋诗词数据集中的诗词中出现的名胜古迹数量进行分析，发现
                <span class="font_style">西湖，庐山，长安，泰山</span>出现的次数较多
            </p>
        </div>
    </div>
</template>


<script>
export default {
    // 图表名称
    name: 'DesignPage',
    methods: {
        myEcharts() {
            // 指定图表的配置项和数据
            const option = {
                title: {text: 'ECharts 入门示例'},
                tooltip: {},
                legend: {data: ['销量']},
                xAxis: {data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]},
                yAxis: {},
                series: [{name: '销量', type: 'bar', data: [5, 20, 36, 10, 10, 20]}]
            };
            // 基于准备好的dom，初始化echarts实例
            const myChart = this.$echarts.init(document.getElementById('BarChartId'));
            // 使用刚指定的配置项和数据显示图表。
            myChart.setOption(option);
        }
    },
    mounted() {
        this.myEcharts();
    }
}
</script>

<!--scoped保证样式只影响当前页面-->
<style scoped>
/*特殊字体样式*/
/*导入自定义字体*/
@import '../assets/css/font.css';

.font_style {
    /*字体样式*/
    font-family: XingKai, serif;
    color: #bd171e;
    /*字体粗细*/
    font-weight: 40;
    /*字体大小*/
    font-size: 40px;
}

/*图表样式*/
.Chart {
    /*图表宽度高度 用来设定图表展示出来的大小 一定要设置*/
    width: 600px;
    height: 400px;
    margin-left: 25%;
    margin-right: -10%;
    flex: 1;
    align-items: center;
}

/*标题样式*/
.title {
    /*字体样式*/
    font-family: XingKai, serif;
    /*字体粗细*/
    font-weight: 40;
    /*字体大小*/
    font-size: 40px;
    color: #e34b0a;
    flex: 1;
    width: 100px;
    margin-top: -10%;
    margin-left: -15%;
    z-index: 1;
}

/*内容样式*/
.content {
    z-index: 1;
    flex: 1;
    display: flex;
    flex-direction: row;
    width: 100px;
    left: 0;
    margin-top: 0;
    margin-left: -60%;
    margin-right: 10%;
}

.main {
    z-index: 10;
    position: fixed;
    display: flex;
    flex-direction: row;
    width: 100%;
    height: 100vh;
    left: 30%;
    top: 0;
    align-items: center;
}

/*背景图设置*/
.mybackground {
    z-index: -1;
    position: relative;
    background-image: url("../assets/data/bg2.jpg");
    width: 100%;
    min-height: 100vh;
    background-size: 100% 100%;
}

</style>