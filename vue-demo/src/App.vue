<template>
    <div>
        <full-page :options="options" ref="fullpage">
            <div class="section">
                <!--第一个页面-->
                <div class="slide">
                    <HomePage PageId="1"/>
                </div>
                <!--第二个页面-->
                <div class="slide">
                    <DesignPage PageId="2"/>
                </div>
            </div>
        </full-page>
    </div>
</template>

<script>
import HomePage from "@/components/HomePage.vue";
import DesignPage from "@/components/DesignPage.vue";

export default {
    name: 'App',
    // 注册页面
    components: {DesignPage, HomePage},
    data() {
        return {
            options: {
                credits: {enabled: false, label: '卧龙凤雏小组出品', position: 'right'},
                // 许可证 不用管
                // licenseKey: "OPEN-SOURCE-GPLV3-LICENSE",
                //是否使用键盘翻页
                keyboardScrolling: true,
                //是否显示导航
                navigation: true,
                //为每个section设置背景色
                sectionsColor: [
                    // 第一个页面的背景色
                    "#f3c59f",
                    // 第二个页面的背景色
                    "#f3c59f",
                    // 第三个页面的背景色
                    "#f3c59f",
                    // 第四个页面的背景色
                    "#f3c59f",
                ],
            }
        }
    },
}

</script>


<style>
/*样式设置*/
</style>
