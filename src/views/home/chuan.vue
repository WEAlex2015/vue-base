<template>

    <div class="chuan-page-box">
        <div class="chuan-page-left">
            <div class="water-stage-box">
                
                <div class="water-stage-chart" ref="waterStageChart" id='waterStageChart'>
                    
                </div>
            </div>

            <div class="water-box">
                
            </div>

            <div class="flow-box">
                
            </div>
        </div>

        <div class="chuan-page-center">
            <div class="map-box">
                <div class="map-content">
                    <div class="map-img">
                       <img src="../../images/center2.png" class="map-img-cls"/>
                   </div>
                </div>
            </div>
        </div>

        <div class="chuan-page-right">
            <div class="rain-box">
                
            </div>

            <div class="electric-box">
                
            </div>

            <div class="power-box">
                
            </div>

        </div>

    </div>
</template>

<script>
    export default {
        data () {
            return {
                
            }
        },
        mounted(){
            this.drawLine();
        },
        methods: {
            drawLine(){
                // 基于准备好的dom，初始化echarts实例
                let myChart = this.$echarts.init(document.getElementById('waterStageChart'));
                // 绘制图表
                myChart.setOption(
                    {
                        title: { 
                            text: '水位' 
                        },
                        tooltip: {},
                        xAxis: {
                            data: ["宝珠寺","紫坪铺","瀑布沟","向家坪","锦屏一级","二滩"]
                        },
                        yAxis: {

                        },
                        series: [{
                            name: '水位',
                            type: 'bar',
                            data: [5, 20, 36, 10, 10, 20]
                        }]
                    });
            }
        },
        created() {
            let me = this;
        }
    }
</script>

<style lang="less">
   .chuan-page-box {
        position: relative;
        width: 100%;
        height: 100%;
        display:-webkit-flex;
        display:flex;
        -webkit-justify-content:space-between;
        justify-content:space-between;
        .chuan-page-left {
            position: relative;
            height: e('calc(100% - 60px)');
            flex: 1;
            margin-left: 10px;
            margin-right: 10px;
            .water-stage-box {
                position: relative;
                height: 30%;
                background-color: #dcdcdc;
                width: 100%;
                .water-stage-chart {
                    position: absolute;
                    width: 100%;
                    height: 100%;
                }
            }
            .water-box {
                position: relative;
                height: 30%;
                margin-top: 10px;
                background-color: #dcdcdc;
            }
            .flow-box {
                position: relative;
                height: 30%;
                margin-top: 10px;
                background-color: #dcdcdc;
            }
        }
        .chuan-page-center {
            position: relative;
            flex: 2;
            height: e('calc(100% - 130px)');
            top: 70px;
            .map-box {
                width: 100%;
                height: 100%;
                .map-content {
                    position: relative;
                    width: 100%;
                    height: 100%;
                    // background-color: #6AC5AC;
                    .map-img {
                        width: 100%;
                        height: 100%;
                        text-align: center;
                        .map-img-cls {
                            width: 100%;
                            height: auto;
                        }
                    }
                }
            }
        }

        .chuan-page-right {
            position: relative;
            flex: 1;
            width: 25%;
            height: e('calc(100% - 60px)');
            margin-left: 10px;
            margin-right: 10px;
            .rain-box {
                position: relative;
                height: 22%;
                background-color: #dcdcdc;
            }
            .electric-box {
                position: relative;
                height: 35%;
                margin-top: 10px;
                background-color: #dcdcdc;
            }
            .power-box {
                position: relative;
                height: 35%;
                margin-top: 10px;
                background-color: #dcdcdc;
            }
        }
   }
</style>
