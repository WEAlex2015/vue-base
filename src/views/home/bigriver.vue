<template>

    <div class="river-page-box">
        <div class="river-page-left">
            <div class="data-box">
                <div class="data-title">
                    <span class="sub-title txt">
                        数据量
                    </span>
                    <span class="sub-title time">
                        数据更新于2018-04-10
                    </span>
                </div>
                <div class="data-data">
                    <div class="today-data">
                        <span class="today today-title">
                            今日数据量
                        </span>
                        <span class="today today-data">
                            1233
                        </span>
                    </div>
                    <div class="total-data">
                        <div class="total total-title">
                            总数据量
                        </div>
                        <div class="total total-data">
                            344
                        </div>
                    </div>
                </div>
            </div>

            <div class="water-box">
                
            </div>

            <div class="flow-box">
                
            </div>
        </div>

        <div class="river-page-center">
            <div class="map-box">
                <div class="map-content">
                    <div class="map-img">
                       <img src="../../images/center.png" class="map-img-cls"/>
                   </div>
                </div>
            </div>
        </div>

        <div class="river-page-right">
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

        },
        methods: {
            
        },
        created() {
            let me = this;
        }
    }
</script>

<style lang="less">
   .river-page-box {
        position: relative;
        width: 100%;
        height: 100%;
        display:-webkit-flex;
        display:flex;
        -webkit-justify-content:space-between;
        justify-content:space-between;
        .river-page-left {
            position: relative;
            height: e('calc(100% - 60px)');
            flex: 1;
            margin-left: 10px;
            margin-right: 10px;
            .data-box {
                position: relative;
                height: 30%;
                background-color: #dcdcdc;
                .data-title {
                    position: relative;
                    height: 50px;
                    top:15px;
                    .sub-title {
                        &.txt{
                            font-size: 22px
                        }
                        &.time{
                            font-size: 16px
                        }
                    }
                }
                .data-data {
                    width: 100%;
                    height: 60%;
                    position: relative;
                    top: 5%;
                    display:-webkit-flex;
                    display:flex;
                    -webkit-justify-content:space-between;
                    justify-content:space-between;
                    .today-data {
                        position: relative;
                        height: 100px;
                        text-align: center;
                        .today {
                            &.today-title {
                                font-size: 16px;
                                position: relative;
                                display:inline-block;
                                width: 100%;
                                height: auto;
                            }
                            &.today-data {
                                font-size: 30px;
                                position: relative;
                                display:inline-block;
                                width: 100%;
                                height: 100%;
                            }
                        }
                    }
                    .total-data {
                        position: relative;
                        height: 100px;
                        text-align: center;
                        .total {
                            &.total-title {
                                font-size: 16px;
                                position: relative;
                                display:inline-block;
                                width: 100%;
                                height: auto;
                            }
                            &.total-data {
                                font-size: 30px;
                                position: relative;
                                display:inline-block;
                                width: 100%;
                                height: 100%;
                            }
                        }
                    }
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
        .river-page-center {
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
                            height: atuo;
                        }
                    }
                }
            }
        }

        .river-page-right {
            position: relative;
            flex: 1;
            width: 25%;
            height: e('calc(100% - 60px)');
            margin-left: 10px;
            margin-right: 10px;
            .rain-box {
                position: relative;
                height: 30%;
                background-color: #dcdcdc;
            }
            .electric-box {
                position: relative;
                height: 30%;
                margin-top: 10px;
                background-color: #dcdcdc;
            }
            .power-box {
                position: relative;
                height: 30%;
                margin-top: 10px;
                background-color: #dcdcdc;
            }
        }
   }
</style>
