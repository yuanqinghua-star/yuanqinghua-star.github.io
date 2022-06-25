---
title: 格点天气预报和实况
tag: [api]
data: grid-weather
version: v7
description: 查看和风天气1公里格点的高精度天气实况、预报API接口开发文档，精确到街道、小区的天气数据，包括：温度、湿度、大气压、天气状况、风力、风向等
---

和风天气1公里格点的高精度天气实况、预报API接口开发文档，精确到街道、小区的天气数据，包括：温度、湿度、大气压、天气状况、风力、风向等。

本数据仅支持中国地区数据。

## 请求URL

{% include request-url.html %}

## 请求参数

请求参数包括必选和可选参数，如不填写可选参数将使用其默认值，参数之间使用`&`进行分隔。

**location** {{ site.data.text.required }}

需要查询地区的以逗号分隔的[经度/纬度坐标](/docs/start/glossary#coordinate)（十进制）。例如： `location=116.41,39.92`

**key** {{ site.data.text.required }}

用户认证密钥，请参考[如何获取你的KEY](/docs/start/get-api-key)。支持[数字签名](/docs/faq/technical#signature-authentication)方式认证。例如：`key=12334567890ABC`

**gzip** {{ site.data.text.optional }}

对API接口进行压缩，可以极大的减少API接口访问延迟，减少缓存空间，提高接口连接成功率。**默认开启gzip**

- `y` 使用gzip方式压缩，默认
- `n` 不使用压缩

**lang** {{ site.data.text.optional }}

多语言设置，支持31种语言，**默认中文**。具体的语言参数值请参考[多语言参数值](/docs/start/language)。

**unit** {{ site.data.text.optional }}

[度量衡单位参数](/docs/start/unit)选择，例如温度选摄氏度或华氏度、公里或英里。**默认公制单位**

- `m` 公制单位，默认
- `i` 英制单位

## 返回数据

| 参数                 | 描述                                                                          | 示例                   |
| -------------------- | ----------------------------------------------------------------------------- | ---------------------- |
| code                 | API状态码，具体含义请参考[状态码](/docs/start/status-code)                    | 200                    |
| updateTime           | 当前[API的最近更新时间](/docs/start/glossary#updatetime)            | 2013-12-30T01:45+08:00 |
| fxLink               | 该城市的{{ page.title }}自适应网页，可嵌入网站或应用                          | http://hfx.link/ae45   |
| now.obsTime          | 格点实况观测时间                                                              | 2013-12-30T01:45+08:00 |
| now.temp             | 格点实况温度                                                                  | 2                      |
| now.icon             | 格点实况天气的图标代码，图标可通过[天气状况和图标](/docs/start/icons)下载     | 101                    |
| now.text             | 格点实况天气状况代码                                                          | 多云                   |
| now.windDir          | 格点实况风向                                                                  | 西北                   |
| now.windScale        | 格点实况风力                                                                  | 1                      |
| now.humidity         | 格点实况相对湿度                                                              | 30                     |
| now.precip           | 格点实况1小时降水量                                                           | 10                     |
| now.pressure         | 格点实况大气压强                                                              | 1030                   |
| daily.fxDate         | 预报日期                                                                      | 2018-05-31             |
| daily.tempMax        | 预报最高温度                                                                  | 4                      |
| daily.tempMin        | 预报最低温度                                                                  | -5                     |
| daily.iconDay        | 预报白天天气状况的图标代码，图标可通过[天气状况和图标](/docs/start/icons)下载 | 100                    |
| daily.iconNight      | 预报夜间天气状况的图标代码，图标可通过[天气状况和图标](/docs/start/icons)下载 | 100                    |
| daily.textDay        | 预报白天天气状况文字描述                                                      | 晴                     |
| daily.textNight      | 预报晚间天气状况文字描述                                                      | 晴                     |
| daily.windDirDay     | 预报白天风向                                                                  | 西北                   |
| daily.windDirNight   | 预报夜间风向                                                                  | 西北                   |
| daily.windScaleDay   | 预报白天风力                                                                  | 3-4                    |
| daily.windScaleNight | 预报夜间风力                                                                  | 3-4                    |
| hourly.fxTime        | 逐小时预报时间                                                                | 2013-12-30T01:45+08:00 |
| hourly.temp          | 逐小时预报温度                                                                | 2                      |
| hourly.icon          | 逐小时预报天气的图标代码，图标可通过[天气状况和图标](/docs/start/icons)下载   | 101                    |
| hourly.text          | 逐小时预报天气状况代码                                                        | 多云                   |
| hourly.windDir       | 逐小时预报风向                                                                | 西北                   |
| hourly.windScale     | 逐小时预报风力                                                                | 3-4                    |
| hourly.precip        | 逐小时预报降水量                                                              | 10                     |
| refer.sources        | 原始数据来源，**可能为空**                                                  |                        |
| refer.license        | 数据许可证                                                  |                        |


## 请求和返回示例

{% include api-response.html %}