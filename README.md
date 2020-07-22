# mini_program_echarts
uni-app开发微信小程序引入Echarts

[Demo 线上地址](https://github.com/theForagingPawns/mini_program_echarts)

1、uni-ec-canvas文件夹复制到pages同级  

    <script>  
    import uniEcCanvas from '../../uni-ec-canvas/uni-ec-canvas.vue'  
    import * as echarts from '../../uni-ec-canvas/echarts'  
    export default {  
        data() {  
            return {  
                ec: {  
			        lazyLoad:true,  
			        option: {  
                        color: ['#3398DB'],  
                        tooltip: {  
                            trigger: 'axis',  
                            axisPointer: {            // 坐标轴指示器，坐标轴触发有效  
                                type: 'shadow'        // 默认为直线，可选为：'line' | 'shadow'  
                            }  
                        },  
                        grid: {  
                            left: '3%',  
                            right: '4%',  
                            bottom: '3%',  
                            containLabel: true  
                        },  
                        xAxis: [  
                            {  
                                type: 'category',  
                                data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun'],  
                                axisTick: {  
                                    alignWithLabel: true  
                                }  
                            }  
                        ],  
                        yAxis: [  
                            {  
                                type: 'value'  
                            }  
                        ],  
                        series: [  
                            {  
                                name: '直接访问',  
                                type: 'bar',  
                                barWidth: '60%',  
                                data: [10, 52, 200, 334, 390, 330, 220]  
                            }  
                        ]  
			        }  
			    }  
            }     
        },  
        onReady () {  
            setTimeout(()=>{  
                console.log(this)  
                console.log(this.$refs)  
                this.$refs['canvas'].init()  
                console.log('延迟加载了')  
            },1000) // 两秒之后延迟加载  
        
            setTimeout(()=>{  
                //this.ec.option.series[0].data = [120, 132, 101, 134, 90, 230, 210]  
                // this.ec.option.xAxis[0].data = [1,2,3,4,5,6,7]  
                // 如果是data数组内的数据 记得用$set  
                console.log('数据更改了')  
            },2000)  
        },  
        components: {  
            uniEcCanvas  
        }  
    }  
    </script>  

3、此包内文件过大，请自行前往 [ECharts 在线定制](http://echarts.baidu.com/builder.html)网页选择自己开发所需相关文件，下载后替换echarts.js文件即可。  
4、本示例的echarts.js文件为自行在上述地址选取的简易柱状图相关js文件，仅按该文档内options配置可用，如有非柱状图需要  请自行前往上述地址重新选取echarts.js文件进行替换。
