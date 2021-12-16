<h1 align="center"> weather </h1>

<p align="center"> 基于高德开放平台的PHP天气信息组件</p>


## 安装

```shell
$ composer require jtipsy/weather -vvv
```

## 配置

```shell
在使用之前，你需要去高德开放平台注册账号，然后创建应用，获取应用的 API Key
```

## 使用

```shell
use Jtipsy\Weather\Weather;
```

```shell
$key = 'api key xxx';
```

```shell
$weather = new Weather($key);
```

## 获取实时天气

```shell
$response = $weather->getWeather('呼和浩特市');
```

示例：

{
    
    "status": "1",
    "count": "1",
    "info": "OK",
    "infocode": "10000",
    "lives": [
        {
            "province": "内蒙古",
            "city": "呼和浩特市",
            "adcode": "150100",
            "weather": "阴",
            "temperature": "-9",
            "winddirection": "北",
            "windpower": "4",
            "humidity": "53",
            "reporttime": "2021-12-16 17:00:39"
        }
    ]
}

## 获取近期天气预报

```shell
$response = $weather->getWeather('呼和浩特市', 'all');
```
示例：

{

    "status": "1",
    "count": "1",
    "info": "OK",
    "infocode": "10000",
    "forecasts": [
        {
            "city": "呼和浩特市",
            "adcode": "150100",
            "province": "内蒙古",
            "reporttime": "2021-12-16 17:00:39",
            "casts": [
                {
                    "date": "2021-12-16",
                    "week": "4",
                    "dayweather": "多云",
                    "nightweather": "晴",
                    "daytemp": "-4",
                    "nighttemp": "-17",
                    "daywind": "西北",
                    "nightwind": "西北",
                    "daypower": "4",
                    "nightpower": "4"
                },
                {
                    "date": "2021-12-17",
                    "week": "5",
                    "dayweather": "晴",
                    "nightweather": "晴",
                    "daytemp": "-8",
                    "nighttemp": "-17",
                    "daywind": "西",
                    "nightwind": "西",
                    "daypower": "4",
                    "nightpower": "4"
                },
                {
                    "date": "2021-12-18",
                    "week": "6",
                    "dayweather": "晴",
                    "nightweather": "晴",
                    "daytemp": "-3",
                    "nighttemp": "-14",
                    "daywind": "西",
                    "nightwind": "西",
                    "daypower": "4",
                    "nightpower": "4"
                },
                {
                    "date": "2021-12-19",
                    "week": "7",
                    "dayweather": "晴",
                    "nightweather": "晴",
                    "daytemp": "-1",
                    "nighttemp": "-11",
                    "daywind": "西",
                    "nightwind": "西",
                    "daypower": "4",
                    "nightpower": "4"
                }
            ]
        }
    ]
}

## 获取XML格式返回值

```shell
$response = $weather->getWeather('呼和浩特市', 'all', 'xml');
```

示例：

```shell
<?xml version="1.0" encoding="UTF-8"?>
<response>
	<status>1</status>
	<count>1</count>
	<info>OK</info>
	<infocode>10000</infocode>
	<lives type="list">
            <live>
                <province>内蒙古</province>
                <city>呼和浩特市</city>
                <adcode>150100</adcode>
                <weather>阴</weather>
                <temperature>-9</temperature>
                <winddirection>北</winddirection>
                <windpower>4</windpower>
                <humidity>53</humidity>
                <reporttime>2021-12-16 17:00:39</reporttime>
            </live>
	</lives>
</response>
```

## 参数说明

```shell
array|string getWeather(string $city, string $type = 'base', string $format = 'json')
```

```shell
$city - 城市名，比如：“呼和浩特市”；
```

```shell
$type - 返回内容类型：base: 返回实况天气 / all: 返回预报天气；
```

```shell
$format - 输出的数据格式，默认为 json 格式，当 output 设置为 “xml” 时，输出的为 XML 格式的数据。
```
## 在Laravel中使用

在 Laravel 中使用也是同样的安装方式，配置写在 config/services.php 中：

    'weather' => [
        'key' => env('WEATHER_API_KEY'),
    ],
    
```shell
然后在 .env 中配置 WEATHER_API_KEY=xxxxxxxxxxx
```


可以用两种方式来获取 Jtipsy\Weather\Weather 实例：

```shell
## 法参数注入
```
    public function edit(Weather $weather) 
    {
        $response = $weather->getWeather('呼和浩特市');
    }

```shell
## 服务名访问
```

    public function edit() 
    {
        $response = app('weather')->getWeather('深圳');
    }
    
## 参考

```shell
高德开放平台天气接口
```

## License

MIT# weather
