<!-- by your name -->
<template>
  <div id="homepage">
    <!--el-row :gutter="20"style="margin-left: 0;margin-right: 0;">
        <el-col :span="16" style="padding:0">
                <el-col :span="8" style="padding:0 20px 0 0;" class="elcol">
                    <el-col :span="24" class="elcol2" style="padding:10px 0">
                        <p class="p1">新增订单</p>
                        <p class="p2">0</p>
                        <p class="p3">待订单(笔)</p>
                    </el-col>
                </el-col>
                <el-col :span="8" style="padding:0 20px 0 0;" class="elcol">
                    <el-col :span="24" class="elcol2" style="padding:10px 0">
                        <p class="p1">金额</p>
                        <p class="p2">19000.0</p>
                        <p class="p3">人民币(元)</p>
                    </el-col>
                </el-col>
                <el-col :span="8" style="padding:0 20px 0 0;" class="elcol">
                    <el-col :span="24" class="elcol2" style="padding:10px 0">
                        <p class="p1">人员</p>
                        <p class="p2">865</p>
                        <p class="p3">人数(人)</p>
                    </el-col>
                </el-col>
                <el-col :span="8" style="padding:0 20px 0 0;" class="elcol">
                    <el-col :span="24" class="elcol2" style="padding:10px 0">
                        <p class="p1">进行中</p>
                        <p class="p2">321</p>
                        <p class="p3">订单(笔)</p>
                    </el-col>
                </el-col>
                <el-col :span="8" style="padding:0 20px 0 0;" class="elcol">
                    <el-col :span="24" class="elcol2" style="padding:10px 0">
                        <p class="p1">已完成</p>
                        <p class="p2">952341</p>
                        <p class="p3">订单(笔)</p>
                    </el-col>
                </el-col>
                <el-col :span="8" style="padding:0 20px 0 0;" class="elcol">
                    <el-col :span="24" class="elcol2" style="padding:10px 0">
                        <p class="p1">已取消</p>
                        <p class="p2">1540</p>
                        <p class="p3">订单(笔)</p>
                    </el-col>
                </el-col>
        </el-col>
        <el-col :span="8" style="padding:0">
            <el-col :span="24" style="padding:0;" class="elcol">
                <el-col :span="24" :style="{height:'380px',width:'100%',backgroundColor: '#F2F6FC'}" id="main">
                    
                </el-col>
            </el-col>
        </el-col>
        <el-col :span="24" class="elcol2" style="padding:10px 0;height:300px;" id="line">
            
        </el-col>
    </el-row-->
  </div>
</template>

<script>
import echarts from 'echarts'
export default {
    name:'homepage',
    data () {
        return {
        }
    },
    methods:{
        install(res){
            this.chart = echarts.init(document.getElementById('main'))
            this.chart.setOption({
                    backgroundColor: 'rgba(219, 203, 213, 0.1)',
                    title: {
                        text: '服务状况',
                        left: 'center',
                        top: 20,
                        textStyle: {
                            color: '#ccc'
                        }
                    },

                    tooltip : {
                        trigger: 'item',
                        formatter: '{a} <br/>{b} : {c} ({d}%)'
                    },

                    visualMap: {
                        show: false,
                        min: 80,
                        max: 600,
                        inRange: {
                            colorLightness: [0, 1]
                        }
                    },
                    series : [
                        {
                            name:'访问来源',
                            type:'pie',
                            radius : '55%',
                            center: ['50%', '50%'],
                            data:[
                                {value:335, name:'订单'},
                                {value:310, name:'人员'},
                                {value:274, name:'服务满意程度'},
                                {value:235, name:'金额'},
                                {value:400, name:'员工收益'}
                            ].sort(function (a, b) { return a.value - b.value }),
                            roseType: 'radius',
                            label: {
                                normal: {
                                    textStyle: {
                                        color: 'rgba(0, 0, 0, 0.8)'
                                    }
                                }
                            },
                            labelLine: {
                                normal: {
                                    lineStyle: {
                                        color: 'rgba(255, 255, 255, 0.3)'
                                    },
                                    smooth: 0.2,
                                    length: 10,
                                    length2: 20
                                }
                            },
                            itemStyle: {
                                normal: {
                                    color: '#c23531',
                                    shadowBlur: 200,
                                    shadowColor: 'rgba(0, 0, 0, 0.5)'
                                }
                            },

                            animationType: 'scale',
                            animationEasing: 'elasticOut',
                            animationDelay: function (idx) {
                                return Math.random() * 200
                            }
                        }
                    ]
                }
            )
        },
        lineinstall(res){
            this.chart = echarts.init(document.getElementById('line'))
            this.chart.setOption({
                title: {
                    text: '发展趋势'
                },
                tooltip: {
                    trigger: 'axis'
                },
                legend: {
                    data:['订单','人员','服务满意程度','金额','员工收益']
                },
                grid: {
                    left: '3%',
                    right: '4%',
                    bottom: '3%',
                    containLabel: true
                },
                toolbox: {
                    feature: {
                        saveAsImage: {}
                    }
                },
                xAxis: {
                    type: 'category',
                    boundaryGap: false,
                    data: ['周一','周二','周三','周四','周五','周六','周日']
                },
                yAxis: {
                    type: 'value'
                },
                series: [
                    {
                        name:'订单',
                        type:'line',
                        stack: '总量',
                        data:[120, 132, 101, 134, 90, 230, 210]
                    },
                    {
                        name:'人员',
                        type:'line',
                        stack: '总量',
                        data:[220, 182, 191, 234, 290, 330, 310]
                    },
                    {
                        name:'服务满意程度',
                        type:'line',
                        stack: '总量',
                        data:[150, 232, 201, 154, 190, 330, 410]
                    },
                    {
                        name:'金额',
                        type:'line',
                        stack: '总量',
                        data:[320, 332, 301, 334, 390, 330, 320]
                    },
                    {
                        name:'员工收益',
                        type:'line',
                        stack: '总量',
                        data:[820, 932, 901, 934, 1290, 1330, 1320]
                    }
                ]
            })
        }
    },
    mounted(){
        // this.install()
        // this.lineinstall()
    }
}

</script>
<style lang='scss' scoped>
#homepage{
    .p1{
        border-bottom:1px solid #EBEEF5;padding:5px 20px 15px;font-family: sans-serif;color: #606266;font-weight: bold;
    }
    .p2{
        padding:16px 20px;font-family: sans-serif;color: #606266;font-size:40px;
    }
    .p3{
        padding:0 20px 10px;font-family: sans-serif;color: #606266;
    }
    .elcol{
        height:180px;margin-bottom:20px;
    }
    .elcol2{
        height:180px;background-color: rgba(219,203,213,0.1);
    }
}
</style>