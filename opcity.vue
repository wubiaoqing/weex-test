//测试安卓下gcanvas标签背景不透明,文字锯齿的问题
<template>
    <scroller>
        <image :src="linkImg.bg" class="bg"></image>
        <div class="chart">
            <gcanvas ref="canvas_holder" style="top: 0; width:750;height:1000;"></gcanvas>
        </div>

    </scroller>
</template>
<style scoped lang="stylus">
    .bg{
        width:750px;
        height:325px;
        position: absolute;
        left:0px;
        top: 0px;
    }
    .chart{
        position: absolute;
        right:0px;
        width:750px;
        top: 0px;
    }
</style>
<script>
    const { enable, WeexBridge, Image: GImage } = require('gcanvas.js');
    export default {
        data(){
            return {
                linkImg: {
                    bg: 'https://ss2.baidu.com/6ONYsjip0QIZ8tyhnq/it/u=1036463264,495157344&fm=173&s=B5A17933145167DCDC1835CC0300A020&w=218&h=146&img.JPEG'
                },
            }
        },
        mounted: function () {
            let ref = this.$refs.canvas_holder;
            ref = enable(ref, {bridge: WeexBridge});
            let ctx = ref.getContext('2d');
            ctx.font="40px Arial";
            ctx.fillText("Hello World!@#$%^&*()_+-=",10,50)
        }
    }
</script>