<template>

    <div class="product-box">

        <div class="left-menu">

            <Menu theme="dark" @on-select="menuSelect" class="menuCls" style="width:150px">

                <Submenu name="1">
                    <template slot="title">
                        电量查询
                    </template>
                    <MenuItem name="1-1">日发电量</MenuItem>
                    <MenuItem name="1-2">线路送电</MenuItem>
                    <MenuItem name="1-3">电量详情</MenuItem>
                </Submenu>

                <Submenu name="2">
                    <template slot="title">
                        实时生产
                    </template>
                    <MenuItem name="2-1">实时生产</MenuItem>
                </Submenu>

                <Submenu name="3">
                    <template slot="title">
                        生产系统
                    </template>
                    <MenuItem name="3-1">生产系统</MenuItem>
                </Submenu>

                <Submenu name="4">
                    <template slot="title">
                        集控日常
                    </template>
                    <MenuItem name="4-1">集控日常</MenuItem>
                </Submenu>

                <Submenu name="5">
                    <template slot="title">
                        生产实况
                    </template>
                    <MenuItem name="5-1">生产实况</MenuItem>
                </Submenu>

                <Submenu name="6">
                    <template slot="title">
                        电网负荷
                    </template>
                    <MenuItem name="6-1">电网负荷</MenuItem>
                </Submenu>
            </Menu>

        </div>

        <div class="tree">
            <span class="">
                大渡河公司
            </span>
            <Tree :data="treeData"></Tree>
        </div>

        <div class="product-table">
            <div class="table-title">
                {{tableTitle}}
            </div>
            <div class="table-area">
                <div class="search-area">
                <span class="">
                    查询日期:
                </span>
                <DatePicker type="date" placeholder="选择日期" style="width: 200px">
                    
                </DatePicker>
                <Button type="ghost" shape="circle" icon="ios-search"></Button>
                </div>
                <div class="table-content">
                    <Table stripe :columns="columns" :data="tableData"></Table>
                </div>
            </div>
            
        </div>

    </div>

</template>


<script>
    export default {
        data () {
            return {
                msg: 'Welcome to Your Vue.js App',
                columns: [],
                tableData: [],
                treeData: [],
                tableTitle: '日发电量'
            }
        },
        mounted(){

        },
        methods: {
            menuSelect (args) {
                console.info(args);
            },
            openMenu (args) {
                console.info(args);
            }
        },
        created() {
            let me = this;
            me.columns = [
                {
                    title: '机组编号',
                    key: 'name'
                },
                {
                    title: '当日发电量(MWh)',
                    key: 'age'
                },
                {
                    title: '月累计(MWh)',
                    key: 'address'
                },
                {
                    title: '自然月累计(MWh)',
                    key: 'address'
                },
                {
                    title: '运行时长(小时)',
                    key: 'address'
                }
            ];
            me.tableData = [
                {
                    name: '铜街子11F',
                    age: 18,
                    address: 'New York No. 1 Lake Park',
                    date: '2016-10-03'
                },
                {
                    name: '铜街子11F',
                    age: 24,
                    address: 'London No. 1 Lake Park',
                    date: '2016-10-01'
                },
                {
                    name: '铜街子11F',
                    age: 30,
                    address: 'Sydney No. 1 Lake Park',
                    date: '2016-10-02'
                },
                {
                    name: '铜街子11F',
                    age: 26,
                    address: 'Ottawa No. 2 Lake Park',
                    date: '2016-10-04'
                },
                {
                    name: '铜街子11F',
                    age: 26,
                    address: 'Ottawa No. 2 Lake Park',
                    date: '2016-10-04'
                },
                {
                    name: '铜街子11F',
                    age: 26,
                    address: 'Ottawa No. 2 Lake Park',
                    date: '2016-10-04'
                }
            ];
            me.treeData = [
                {
                    title: '龚电总厂',
                    expand: true,
                    children: [
                        {
                            title: '龚嘴电站',
                            expand: true,
                            children: [
                                
                            ]
                        },
                        {
                            title: '枕头坝一级电站',
                            expand: true,
                            children: [
                                
                            ]
                        }
                    ]
                },
                {
                    title: '瀑电总厂',
                    expand: false,
                    children: [
                        {
                            title: '瀑电总厂1',
                            expand: false,
                            children: [
                                
                            ]
                        },
                        {
                            title: '瀑电总厂2',
                            expand: false,
                            children: [
                                
                            ]
                        }
                    ]
                },
                {
                    title: '枕头坝电厂',
                    expand: false,
                    children: [
                        {
                            title: '枕头坝电厂1',
                            expand: false,
                            children: [
                                
                            ]
                        },
                        {
                            title: '枕头坝电厂2',
                            expand: false,
                            children: [
                                
                            ]
                        }
                    ]
                },
            ];
        }
    }
</script>

<style lang="less">

    .product-box {
        position: relative;
        top: 0px;
        display:-webkit-flex;
        display:flex;
        -webkit-justify-content: flex-start;
        justify-content: flex-start;
        width: 100%;
        height: 100%;
        .left-menu {
            position: relative;
            background-color: #495060;
            flex: 1;
        }
        .tree {
            position: relative;
            background-color:  #dcdcdc;
            flex: 1;
        }
        .product-table {
            position: relative;
            right: 10px;
            left: 0px;
            background-color: #19A5D8;
            flex: 7;
            .table-title {
                position: relative;
                top: 10px;
                left: 30px;
                width: 95%;
                font-size: 16px;
            }
            .table-area {
                position: relative;
                background-color: #157CAD;
                top: 20px;
                left: 0px;
                margin-right:10px;
                margin-left:10px;
                height: 100%;
                .search-area {
                    position: relative;
                    top: 20px;
                    left: 30px;
                    width: 95%;
                    font-size: 14px;
                }
                .table-content {
                    position: relative;
                    top: 30px;
                    left: 30px;
                    width: 95%;
                }
            }
        }
    }
</style>
