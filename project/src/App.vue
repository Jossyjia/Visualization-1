<template>
    <div>
        <full-page :options="options" ref="page">
            <div class="section">
                <div class="slide">
                    <HomePage PageId="1" />
                </div>
                <div class="slide">
                    <IntroProject PageId="2" />
                </div>
                <div class="slide">
                    <NMGraph PageId="3" />
                </div>
                <div class="slide">
                    <PMGraph PageId="4" />
                </div>
                <div class="slide">
                    <NM_BarGraph PageId="5"/>
                </div>
                <div class="slide">
                    <PM_BarGraph PageId="6"/>
                </div>
                <div class="slide">
                    <ColorGraph PageId="7" />
                </div>
                <div class="slide">
                    <RebuildGraph PageId="8" />
                </div>
                <div class="slide">
                    <QDGraph PageId="9" />
                </div>
                <!-- <div class="slide">
                    <QMGraph PageId="8" />
                </div> -->
                <div class="slide">
                    <WordCloud PageId="10" />
                </div>
                <div class="slide">
                    <Geography PageId="11" />
                </div>
                <div class="slide">
                    <RelicsGraph PageId="12" />
                </div>
                <div class="slide">
                    <ThanksPage PageId="12" />
                </div>
            </div>
        </full-page>
    </div>
</template>

<script>
import HomePage from "@/components/HomePage.vue";
import RelicsGraph from "@/components/RelicsGraph.vue";
import RebuildGraph from "@/components/RebuildGraph.vue";
import ColorGraph from "@/components/ColorGraph.vue";
import NMGraph from "@/components/NM.vue";
import PMGraph from "@/components/PM.vue";
import QDGraph from "@/components/QD.vue";
// import QMGraph from "@/components/QM.vue";
import WordCloud from "@/components/WordCloud.vue";
import Geography from "@/components/Geography.vue";
import NM_BarGraph from "@/components/NM_Bar.vue";
import PM_BarGraph from "@/components/PM_Bar.vue";
import IntroProject from "@/components/Intro.vue";
import ThanksPage from "@/components/ThanksPage.vue";

export default {
    name: 'App',
    // 注册页面
    components: { PM_BarGraph,IntroProject,ThanksPage,
        NM_BarGraph, PMGraph, NMGraph, ColorGraph, RelicsGraph, HomePage, RebuildGraph, QDGraph, WordCloud, Geography },
    data() {
        return {
            options: {
                credits: { enabled: false, label: '卧龙凤雏小组出品', position: 'right' },
                //是否使用键盘翻页
                keyboardScrolling: true,
                //是否显示导航
                navigation: false,
                //为每个section设置背景色
                sectionsColor: [],
                //是否显示箭头
                controlArrows: false
            }
        }
    },
}

</script>


<style>
/*样式设置*/
</style>
