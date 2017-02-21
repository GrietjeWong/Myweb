---
layout: post
title: "我的2016年读书数据"
date: 2017-01-10
categories:
  - DataAnalysis数据分析
description:
image: /img/james-tarbotton-367.jpg
image-sm:
---
核心技术：Echarts<br/>

最近几年读的书真是越来越有征兆。前几天在GitHub上git到一个很有意思的图表展示工具，一玩就上瘾了。呐～废话不多说，先上个图：

<html>
<head>
    <meta charset="utf-8">
    <title>ECharts</title>
    <!-- 引入 echarts.js -->
    <script src="/assets/js/echarts.js"></script>
</head>
<body>
    <!-- 为ECharts准备一个具备大小（宽高）的Dom -->
    <div id="main" style="width: 750px;height:400px;"></div>
    <script type="text/javascript">
        // 基于准备好的dom，初始化echarts实例
        var myChart = echarts.init(document.getElementById('main'));

        // 指定图表的配置项和数据
        var xData = function() {
    var data = ["Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"];
    for (var i = 1; i < 13; i++) {
        //data.push(i + "月份");
        data.push(data[i]);
    }
    return data;
}();

option = {
    backgroundColor: "#FAFAFA",
    "title": {
        "text": "2016 Reading Records",
        "subtext": "BY Zhendi Huang",
       x: "6%",

        textStyle: {
            color: '#010D13',
            fontSize: '22',
        },
        subtextStyle: {
            color: '#90979c',
            fontSize: '16',

        },
    },
    "tooltip": {
        "trigger": "axis",
        "axisPointer": {
            "type": "shadow",
            textStyle: {
                color: "#000000"
            }

        },
    },
    "grid": {
        "borderWidth":0,
        "top": 210,
        "bottom": 90,
        textStyle: {
            color: "#fff"
        }
    },
    "legend": {
        x: '70%',
        top: '11%',
        textStyle: {
            color: '#90979c',
        },
        "data": ['Personal Development', 'Professional', '平均']
    },


    "calculable": true,
    "xAxis": [{
        "type": "category",
        "axisLine": {
            lineStyle: {
                color: '#90979c'
            }
        },
        "splitLine": {
            "show": false
        },
        "axisTick": {
            "show": false
        },
        "splitArea": {
            "show": false
        },
        "axisLabel": {
            "interval": 0,

        },
        "data": xData,
    }],
    "yAxis": [{
        "type": "value",
        "splitLine": {
            "show": false
        },
        "axisLine": {
            lineStyle: {
                color: '#90979c'
            }
        },
        "axisTick": {
            "show": false
        },
        "axisLabel": {
            "interval": 0,

        },
        "splitArea": {
            "show": false
        },

    }],
    "dataZoom": [{
        "show": true,
        "height": 30,
        "xAxisIndex": [
            0
        ],
        bottom: 30,
        "start": 10,
        "end": 80,
        handleIcon: 'path://M306.1,413c0,2.2-1.8,4-4,4h-59.8c-2.2,0-4-1.8-4-4V200.8c0-2.2,1.8-4,4-4h59.8c2.2,0,4,1.8,4,4V413z',
        handleSize: '100%',
        handleStyle: {
            color: "#d3dee5",

        },
        textStyle: {
            color: "#90979c"
        },
        borderColor: "#90979c"


    }, {
        "type": "inside",
        "show": true,
        "height": 15,
        "start": 1,
        "end": 35
    }],
    "series": [{
            "name": "Personal Development",
            "type": "bar",
            "stack": "总量",
            "barMaxWidth": 35,
            "barGap": "10%",
            "itemStyle": {
                "normal": {
                    "color": "#1C688E",
                    "label": {
                        "show": true,
                        "textStyle": {
                            "color": "#FFFFFF"
                        },
                        "position": "insideTop",
                        formatter: function(p) {
                            return p.value > 0 ? (p.value) : '';
                        }
                    }
                }
            },
            "data": [
                4,
                3,
                3,
                2,
                3,
                1,
                5,
                3,
                2,
                2,
                2,
                3
            ],
        },

        {
            "name": "Professional",
            "type": "bar",
            "stack": "总量",
            "itemStyle": {
                "normal": {
                    "color": "#A0CCE2",
                    "barBorderRadius": 0,
                    "label": {
                        "show": true,
                        "textStyle": {
                            "color": "#90979c"
                        },
                        "position": "top",
                        formatter: function(p) {
                            return p.value > 0 ? (p.value) : '';
                        }
                    }
                }
            },
            "data": [
                2,
                3,
                1,
                1,
                2,
                1,
                2,
                3,
                4,
                3,
                2,
                0
            ]
        }, {
            "name": "Amount",
            "type": "line",
            "stack": "总量",
            symbolSize: 10,
            symbol: 'circle',
            "itemStyle": {
                "normal": {
                    "color": "#1C688E",
                    "barBorderRadius": 0,
                    "label": {
                        "show": true,
                        "position": "top",
                        formatter: function(p) {
                            return p.value > 0 ? (p.value) : '';
                        }
                    }
                }
            },
            "data": [
                6,
                6,
                4,
                3,
                5,
                2,
                7,
                5,
                6,
                5,
                4,
                3
            ]
        },
    ]
}
        // 使用刚指定的配置项和数据显示图表。
        myChart.setOption(option);
    </script>
</body>
</html>


新旧网站的替换，内容搬运中.....

<ul>

</ul>

<ol>

</ol>

<h3>Subway tile</h3>


<figure>

</figure>


<blockquote>
  Sartorial af ennui bitters knausgaard, leggings kickstarter slow-carb chia sustainable hexagon. Prism 3 wolf moon occupy ramps wayfarers tumblr narwhal 90's.
  <cite>Man braid</cite>
</blockquote>

<h4>Subway tile</h4>


<figure>
  <img src="https://unsplash.it/2000/1200?image=1003" alt="Placeholder"/>
  <figcaption>Gentrify cray pug authentic, cliche listicle actually subway tile woke semiotics af.</figcaption>
</figure>
