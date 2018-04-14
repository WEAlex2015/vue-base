<template>

    <div class="main">
        <div class="container">
            <div class="header">
                <div class="datetime">
                    <span class="time" >{{time}}</span>
                    &nbsp;&nbsp;
                    <span class="date" >{{date}}</span>
                </div>
                <div class="app-title">
                    大渡河梯级电站共享平台
                </div>

                <div class="menu-btn">
                    <Button type="text" :class="[btnHomeClass]" @click="topMenuClick('home')">
                        <Icon type="home" size="26"></Icon>
                    </Button>
                    <Button type="text" :class="[btnReportClass]" @click="topMenuClick('report')">
                        <Icon type="ios-monitor" size="26"></Icon>
                    </Button>
                    <Tooltip content="有3条未读消息">
                        <Button type="text" :class="[btnTipsClass]" @click="topMenuClick('message')">
                            <Badge count="3" overflow-count="99">
                                <Icon type="ios-bell" size="26"></Icon>
                            </Badge>
                        </Button>
                    </Tooltip>
                    <Button type="text" :class="[btnOutClass]" @click="topMenuClick('out')">
                        <Icon type="power" size="26"></Icon>
                    </Button>
                </div>
            </div>
            <div class="btn-box" v-show="isShowBtn">
                <div class="title">
                    <span class="txt">
                        流域信息共享 |
                    </span>
                    <span class="txt sub">
                        <span class="name">
                            {{station.name}}
                        </span>
                        流域目前已接入电站
                        <span class="number">
                            {{station.number}}
                        </span>
                        个
                    </span>
                </div>
                <div class="map-btn">
                    <div class="map-btn-bg">
                         <Button type="text" :class="[river]" @click="mapBtnClick('river')">    大渡河
                         </Button>
                        <Button type="text" :class="[chuan]" @click="mapBtnClick('chuan')">
                            全川
                        </Button>
                    </div>
                   
                </div>
            </div>
            <div class="content-body"> 
                <component :is="nowComp"></component>
            </div>
        </div>
    </div>
</template>


<script>

    import bigriver from "./home/bigriver.vue";
    import chuan from "./home/chuan.vue";
    import report from "./report/report.vue";
    import message from "./message/message.vue";
    import { mapGetters } from 'vuex';

    export default {

        computed: mapGetters({
            testData: 'testData',
        }),

        components: {
            'bigriver': bigriver,
            'chuan': chuan,
            'report': report,
            'message': message,
        },

        data () {
            return {
                nowComp: "bigriver",
                time:'',
                date:'',
                btnHomeClass: 'active',
                btnReportClass: '',
                btnTipsClass: '',
                btnOutClass: '',
                river : 'active',
                chuan: '',
                station : {
                    name: '大渡河',
                    number: '23'
                },
                isShowBtn: true,
                
            }
        },
        mounted(){
        },
        watch:{
            "testData":function (val) {
                console.info(val);
            }
        },
        methods: {
            topMenuClick(args) {
                let me = this;
                switch (args) {
                    case 'home' : 
                        me.btnHomeClass = 'active';
                        me.btnReportClass = '';
                        me.btnTipsClass = '';
                        me.btnOutClass = '';
                        me.nowComp = 'bigriver';
                        me.isShowBtn = true;
                        break;
                    case 'report' : 
                        me.btnHomeClass = '';
                        me.btnReportClass = 'active';
                        me.btnTipsClass = '';
                        me.btnOutClass = '';
                        me.nowComp = 'report';
                        me.isShowBtn = false;
                        break;
                    case 'message' : 
                        me.btnHomeClass = '';
                        me.btnReportClass = '';
                        me.btnTipsClass = 'active';
                        me.btnOutClass = '';
                        me.isShowReport = false;
                        me.isShowBtn = false;
                        me.nowComp = 'message';
                        break;
                    case 'out' : 
                        me.btnHomeClass = '';
                        me.btnReportClass = '';
                        me.btnTipsClass = '';
                        me.btnOutClass = 'active';
                        me.isShowBtn = false;
                        break;
                    default:
                        break;
                }
            },
            mapBtnClick (type) {
                let me = this;
                switch (type) {
                    case 'river':
                        me.river = 'active';
                        me.chuan = '';
                        me.nowComp = 'bigriver'
                        me.station = {
                            name: '大渡河',
                            number: '23'
                        }
                        break;
                    case 'chuan':
                        me.river = '';
                        me.chuan = 'active';
                        me.nowComp = 'chuan'
                        me.station = {
                            name: '全川',
                            number: '34'
                        }
                        break;
                    default:
                        break;
                }
            },
            /* 头部时间控件 */
            initTimer() {
                let me = this;
                var date = new Date();
                var h = date.getHours();
                h = h > 9 ? h : '0' + h;
                var m = date.getMinutes();
                m = m > 9 ? m : '0' + m;
                var s = date.getSeconds();
                s = s > 9 ? s : '0' + s;
                me.time = h + '：' + m + '：' + s;

                var y = date.getFullYear();
                var M = date.getMonth();
                M = M > 9 ? M : '0' + M;
                var d = date.getDate();
                d = d > 9 ? d : '0' + d;
                me.date = y + '-' + M + '-' + d;
                setTimeout(function () {
                    me.initTimer();
                }, 1000);
            },
            test() {
                let me = this;
                console.info('test func');
                me.$store.dispatch('test', {reqData: {}});
            }
        },
        created() {
            let me = this;
            me.initTimer();
            console.info(me.$store);
            me.test();
        }
    }
</script>

<style lang="less">
    .main {
        height: 100%;
        .container {
            position: relative;
            width: 100%;
            height: 100%;
            .content-body {
                position: relative;
                top: 5px;
                height: 100%;
            }
            .header {
                position: relative;
                font-size: 26px;
                top: 5px;
                left: 0px;
                text-align: center;
                display:-webkit-flex;
                display:flex;
                -webkit-justify-content:space-between;
                justify-content:space-between;
                .datetime {
                    position: relative;
                    height: 30px;
                    font-size: 16px;
                    width: 300px;
                }
                .app-title {
                    position: relative;
                    height: 30px;
                    width: 300px;
                    
                }
                .menu-btn {
                    position: relative;
                    height: 30px;
                    right: 5px;
                    width: 300px;
                    .ivu-btn-text {
                        &:focus {
                            box-shadow: 0 0 0 0;
                        }
                    }
                }

            }
            .btn-box {
                position:absolute; 
                z-index:1;
                height: 70px;
                width: e('calc(100% * 48.5%)');
                left: 26%;
                display:-webkit-flex;
                display:flex;
                -webkit-justify-content:space-between;
                justify-content:space-between;
                // background-color: #9DBFE3;
                .title {
                    position: relative;
                    text-align: left;
                    .txt {
                        position: relative;
                        left: 0px;
                        top: 20px;
                        font-size: 20px;
                        &.sub {
                            font-size: 12px;
                            .number {
                                color: red;
                            }
                            .name {
                                color: red;
                            }
                        }
                    }
                }
                
                .map-btn {
                    position: relative;
                    .map-btn-bg {
                        position: relative;
                        width: 164px;
                        height: 32px;
                        color: #ffffff;
                        background-color: #113F66;
                        border-radius:35px;
                        text-align: center;
                        top: 20px;
                    }
                    .river {

                    }
                    .ivu-btn {
                        transition: none;
                    }
                    
                    .ivu-btn-text {
                        color: #70889e;
                        width: 80px;
                        position: relative;
                        font-size: 16px;
                        height: 40px;
                        top: -5px;
                        &.active {
                            border-radius: 25px;
                            color: #FFFFFF;
                            height: 40px;
                            // background-color: #37b4dc;
                            background: -webkit-linear-gradient(  #47dce8,#2d9cd4 );
                            background: -o-linear-gradient( #47dce8,#2d9cd4);
                            background: -moz-linear-gradient( #47dce8,#2d9cd4);
                            background: linear-gradient( #47dce8,#2d9cd4);
                            box-shadow: 0px 1px 0px 2px rgba(17,63,102,0.6);
                        }
                        &:focus {
                            // box-shadow: 0px 1px 0px 2px rgba(17,63,102,1);
                        }
                        &:hover {
                        }
                    }
                }
            }
        }
    } 
    
</style>
