DesignPage.vue
<template>
    <div class="mybackground"></div>
    <div class="main">
        <div id="RebuildGraph" class="RebuildGraphChart"></div>
        <div class="title">
            <p class="font_style2">
                敦煌历史上，僧人和僧团对莫高窟的创建、管理和维护做出过重大贡献，大族和官宦是莫高窟薪火相传的中坚力量，而广大民众则是莫高窟振兴不衰的历史的主体。前人早在１０００年前就做出定论：莫高窟是因“君臣缔构而兴隆，道俗镌妆而信仰”；先有君臣，后有道俗；而营造目的则是“君王万岁，社稷千秋”，为君臣缔构之目的，道俗镌妆之追求。

                莫高窟的壁画一开始就以中国传统的线描和晕染相结合的手法为主，又随着时代的前进而不断发展。人们一走进洞窟便有各种各样的感受：十六国的古朴典雅，北魏的飘逸清秀，北周的圆浑明暗，隋代的丽雅精细，唐代前期的灿烂辉煌……其不断发展，蓬勃向上的艺术生命力，给人们以美好的享受。
            </p>
        </div>
    </div>
</template>


<script>
export default {
    // 图表名称
    name: 'RebuildGraph',
    methods: {
        myEcharts() {
            const RebuildGraphChart = this.$echarts.init(document.getElementById('RebuildGraph'));
            var option;
            const names = ['北魏', '西魏', '北周', '隋', '初唐', '盛唐', '中唐吐蕃', '晚唐', '五代', '宋', '沙洲回鹘', '西夏', '蒙古/元', '清'];
            option = {
                title: { text: '开放参观的莫高窟各洞窟开凿与重修年代表' },
                color: ['#356c9d', '#206864', '#5da39d', '#a2d2e2'],
                tooltip: {
                    trigger: 'axis',
                    axisPointer: {
                        type: 'cross',
                        label: {
                            backgroundColor: '#6a7985'
                        }
                    }
                },
                legend: {
                    data: ['开凿', '第一次重修', '第二次重修', '第三次重修']
                },
                toolbox: {
                    feature: {
                        saveAsImage: {}
                    }
                },
                grid: {
                    left: '3%',
                    right: '4%',
                    bottom: '3%',
                    containLabel: true
                },
                xAxis: [
                    {
                        type: 'category',
                        boundaryGap: false,
                        data: ['9', '12', '16', '17', '23', '25', '29', '44', '46', '61', '66', '71', '79', '96',
                            '100', '103', '130', '138', '146', '148', '152', '171', '201', '202', '203', '204',
                            '205', '209', '237', '244', '246', '249', '251', '257', '259', '290', '292', '296',
                            '311', '314', '323', '328', '329', '331', '332', '334', '335', '340', '384', '386',
                            '390', '397', '401', '407', '409', '419', '420', '428', '445'
                        ]
                    }
                ],
                yAxis: [
                    {
                        type: 'category',
                        axisLabel: {
                            margin: 30,
                            fontSize: 16
                        },
                        inverse: false,
                        data: names
                    }
                ],
                series: [
                    {
                        name: '开凿',
                        type: 'line',

                        areaStyle: {},
                        emphasis: {
                            focus: 'series'
                        },
                        data: ['晚唐', '晚唐', '晚唐', '晚唐', '盛唐', '宋', '晚唐', '盛唐', '盛唐', '五代', '盛唐',
                            '初唐', '盛唐', '初唐', '五代', '盛唐', '盛唐', '晚唐', '五代', '盛唐', '宋', '盛唐',
                            '中唐吐蕃', '初唐', '初唐', '初唐', '初唐', '初唐', '中唐吐蕃', '隋', '西魏', '西魏',
                            '北魏', '北魏', '北魏', '北周', '隋', '北周', '隋', '隋', '盛唐', '初唐', '初唐', '初唐',
                            '初唐', '初唐', '初唐', '初唐', '盛唐', '初唐', '隋', '隋', '隋', '隋', '沙洲回鹘', '隋',
                            '隋', '北周', '盛唐'
                        ]
                    },
                    {
                        name: '第一次重修',
                        type: 'line',
                        stack: 'Total',
                        areaStyle: {},
                        emphasis: {
                            focus: 'series'
                        },
                        data: ['宋', '五代', '清', '晚唐', '中唐吐蕃', '西夏', '清', '中唐吐蕃', '五代', '蒙古/元',
                            '盛唐', '初唐', '五代', '清', '清', '清', '西夏', '五代', '宋', '晚唐', '西夏', '宋',
                            '宋', '宋', '宋', '五代', '盛唐', '五代', '沙洲回鹘', '五代', '西夏', '清', '五代',
                            '宋', '宋', '宋', '初唐', '五代', '五代', '西夏', '西夏', '五代', '五代', '五代', '五代',
                            '五代', '中唐吐蕃', '中唐吐蕃', '中唐吐蕃', '中唐吐蕃', '五代', '五代', '五代', '宋', '清',
                            '西夏', '西夏', '五代', '五代'
                        ]
                    },
                    {
                        name: '第二次重修',
                        type: 'line',
                        stack: 'Total',
                        areaStyle: {},
                        emphasis: {
                            focus: 'series'
                        },
                        data: ['蒙古/元', '清', '清', '晚唐', '五代', '清', '清', '五代', '宋', '蒙古/元', '盛唐',
                            '初唐', '五代', '清', '清', '清', '西夏', '蒙古/元', '蒙古/元', '沙洲回鹘', '清', '清',
                            '宋', '清', '宋', '宋', '中唐吐蕃', '清', '清', '沙洲回鹘', '西夏', '清', '清', '宋',
                            '宋', '宋', '盛唐', '清', '清', '清', '清', '西夏', '清', '清', '蒙古/元', '清', '宋',
                            '晚唐', '五代', '五代', '清', '清', '清', '清', '清', '西夏', '西夏', '五代', '西夏'
                        ]
                    },
                    {
                        name: '第三次重修',
                        type: 'line',

                        areaStyle: {},
                        emphasis: {
                            focus: 'series'
                        },
                        data: ['清', '清', '清', '晚唐', '清', '清', '清', '五代', '宋', '蒙古/元', '盛唐', '初唐',
                            '五代', '清', '清', '清', '西夏', '清', '清', '清', '清', '清', '宋', '清', '宋', '清',
                            '五代', '清', '清', '沙洲回鹘', '西夏', '清', '清', '宋', '宋', '宋', '五代', '清', '清',
                            '清', '清', '西夏', '清', '清', '清', '清', '蒙古/元', '蒙古/元', '清', '清', '清', '清',
                            '清', '清', '清', '西夏', '西夏', '五代', '西夏'
                        ]
                    }
                ]
            };
            RebuildGraphChart.setOption(option);
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


/*图表样式*/
.RebuildGraphChart {
    /*图表宽度高度 用来设定图表展示出来的大小 一定要设置*/
    width: 1600px;
    height: 600px;
    background-size: cover;
    margin-left: 450px;
    margin-top: 50px;
    margin-right: 0;
    /*margin-right: -10%;*/
    /*flex: 1;*/
    /*align-items: center;*/
}

/*标题样式*/
.title {
    position: fixed;
    top: 10%;
    margin-left: 590px;
    margin-top: 540px;
    margin-bottom: 20px;
    width: 1400px;
    /* 例如，设置宽度为 800 像素 */
    height: 600px;
    /* 例如，设置高度为 600 像素 */
}

.font_style2 {
    /*字体样式*/
    font-family: 'Fengyun', serif;
    /*字体粗细*/
    font-weight: 40;
    /*字体大小*/
    font-size: 25px;
    color: #4a4a4a;
    /* 深灰色，更柔和的黑色 */
    /* 行高 */
    line-height: 1.2;
    /* 文本自动换行 */
    word-wrap: break-word;
    overflow-wrap: break-word;
    /* 边缘留白 */
    padding: 25px;
    /* 根据需要调整内边距 */
    margin: 20px;
    /* 根据需要调整外边距 */
}



.main {
    z-index: 10;
    position: fixed;
    display: flex;
    flex-direction: row;
    width: 11600px;
    height: 100vh;
    left: 9800px;
    top: 0;
    /*align-items: center;*/
}

/*背景图设置*/
.mybackground {
    z-index: -1;
    position: relative;
    background-image: url("../assets/data/bg6.png");
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