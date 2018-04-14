<template>

    <div class="quanchuanDiv">
       <div id="myChart" class="chart1"></div>

    </div>

</template>

<style type="text/css">
    
    .chart1 {
        width: 300px;
        height: 300px
    }

</style>
<script>
    export default {
        data () {
            return {
              msg: 'Welcome to Your Vue.js App'
            }
        },
        mounted(){
            this.drawLine();
          },
        methods: {
            drawLine(){
                // 基于准备好的dom，初始化echarts实例
                let myChart = this.$echarts.init(document.getElementById('myChart'));
                // 绘制图表
                myChart.setOption(
                    {
                        title: { 
                            text: '电力市场' 
                        },
                        tooltip: {},
                        xAxis: {
                            data: ["衬衫","羊毛衫","雪纺衫","裤子","高跟鞋","袜子"]
                        },
                        yAxis: {

                        },
                        series: [{
                            name: '销量',
                            type: 'bar',
                            data: [4, 22, 33, 22, 33, 11]
                        }]
                    });
            }
        },
        created() {
            let me = this;
        }
    }
</script>
