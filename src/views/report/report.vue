<template>

    <div class="report-box">
        <div class="report-menu-box">
            <Menu mode="horizontal" active-name="product" @on-select="reportSelect">
                <MenuItem name="infoshare">
                    <Icon type="ios-paper"></Icon>
                    流域信息共享
                </MenuItem>
                <MenuItem name="product">
                    <Icon type="ios-people"></Icon>
                    电力生产
                </MenuItem>
                <MenuItem name="market">
                    <Icon type="ios-people"></Icon>
                    电力市场
                </MenuItem>
                <MenuItem name="forrain">
                    <Icon type="settings"></Icon>
                    降雨预报
                </MenuItem>
                <MenuItem name="sendreport">
                    <Icon type="settings"></Icon>
                    报表上送
                </MenuItem>
                <MenuItem name="analysis">
                    <Icon type="settings"></Icon>
                    指标分析
                </MenuItem>
            </Menu>
        </div>
        <div class="report-content">
            <component :is="reportNowComp"></component>
        </div>
    </div>

</template>


<script>
    
    import product from "./product/product.vue";
    import market from "./market/market.vue";
    import infoshare from "./infoshare/infoshare.vue";

    export default {

        components: {
            'product': product,
            'market': market,
            'infoshare': infoshare,
        },

        data () {
            return {
              msg: 'Welcome to Your Vue.js App',
              reportNowComp: 'product'
            }
        },
        mounted(){
        },
        methods: {
            reportSelect (args) {
                let me = this;
                me.reportNowComp = args;
            },
        },
        created() {
            let me = this;
        }
    }
</script>

<style lang="less">
    .report-box {
        height: e('calc(100% - 110px)');
        .report-menu-box {
            width: 100%;
            height: 50px;
            background-color: #dcdcdc;
            position: relative;
            .ivu-menu {
                position: relative;
                height: 50px;
            }
        }
        .report-content {
            height: 100%;
        }
    }
    
</style>
