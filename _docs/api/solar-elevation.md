---
title: 太阳高度
tag: [api]
data: astronomy
version: v7
description: 查看和风天气太阳高度角API接口开发文档，支持任意时间点的全球太阳高度及方位角接口，为安全和智能驾驶、房屋建设提供数据支持
---

任意时间点的全球太阳高度及方位角接口，为安全和智能驾驶、房屋建设提供数据支持。

## 请求URL

**太阳高度角** **HTTP GET**{:.httpget}

* 商业版 `https://geoapi.heweather.net/v7/solar-elevation-angle?{请求参数}`{:.requesturl }

{% include request-url.html %}

## 请求参数

请求参数包括必选和可选参数，如不填写可选参数将使用其默认值，参数之间使用`&`进行分隔。

location {{ site.data.text.required }}

太阳高度角是基于经纬度测量的，需要填写具体的坐标，填写格式：经度,纬度（经度在前纬度在后，英文`,`分隔，十进制格式，北纬东经为正，南纬西经为负）。例如：`location=116.41,39.92`

**data** {{ site.data.text.required }}
    
查询日期，格式为yyyyMMdd，例如 `date=20170809`

**time** {{ site.data.text.required }}
    
 查询时间，格式为HHmm，24 时制，例如 `time=1230`

**tz** {{ site.data.text.required }}
    
查询地区所在时区，例如`tz=0800`或`tz=-0530`

**alt** {{ site.data.text.required }}
    
海拔高度，单位为米，例如`alt=43`

**key** {{ site.data.text.required }}

用户认证key，请参考[如何获取你的KEY](/docs/start/get-api-key)。支持[数字签名](/docs/faq/technical#signature-authentication)方式进行认证，推荐使用。例如 `key=123456789ABC`

## 返回数据

| 参数                 | 描述                           | 示例值 |
| -------------------- | ------------------------------ | ------ |
| code                 | API状态码，具体含义请参考[状态码](/docs/start/status-code)      | 200    |
| solar.elevationAngle | 太阳高度角                     | 89     |
| solar.azimuthAngle   | 太阳方位角，正北顺时针方向角度 | 190    |
| solar.hour           | 太阳时                         | 0923   |
| hour.angle           | 时角                           | -45.5  |
| refer.sources        | 原始数据来源，**可能为空**   |        |
| refer.license        | 数据许可证   |        |

## 请求和返回示例

{% include api-response.html %}