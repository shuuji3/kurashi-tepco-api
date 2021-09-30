# kurashi-tepco-api

[![npm](https://img.shields.io/npm/v/kurashi-tepco-api.svg)](https://www.npmjs.com/package/kurashi-tepco-api) [![Node.js CI status](https://github.com/shuuji3/kurashi-tepco-api/workflows/Node.js%20CI/badge.svg)](https://github.com/shuuji3/kurashi-tepco-api/actions)

## Note

We can use [sh-kawakami/tepco-watt-stats: くらしTEPCOのページから電力使用量情報を取得する](https://github.com/sh-kawakami/tepco-watt-stats). 

## TEPCO API endpoint

- hourly data
  - csv [https://www.kurashi.tepco.co.jp/pf/ja/pc/mypage/learn/comparison.page?ReqID=CsvDL&year=2021&month=9&day=28](https://www.kurashi.tepco.co.jp/pf/ja/pc/mypage/learn/comparison.page?ReqID=CsvDL&year=2021&month=9&day=28)
  - json: [https://www.kurashi.tepco.co.jp/pf/ja/res/mypage/learn/comparison.page?\_ajax_request=1&year=2021&month=9&day=28](https://www.kurashi.tepco.co.jp/pf/ja/res/mypage/learn/comparison.page?_ajax_request=1&year=2021&month=9&day=28)
- daily
  - csv [https://www.kurashi.tepco.co.jp/pf/ja/pc/mypage/learn/comparison.page?ReqID=CsvDL&year=2021&month=9](https://www.kurashi.tepco.co.jp/pf/ja/pc/mypage/learn/comparison.page?ReqID=CsvDL&year=2021&month=9)
  - json [https://www.kurashi.tepco.co.jp/pf/ja/res/mypage/learn/comparison.page?\_ajax_request=1&year=2021&month=9](https://www.kurashi.tepco.co.jp/pf/ja/res/mypage/learn/comparison.page?_ajax_request=1&year=2021&month=9)
- monthly
  - csv [https://www.kurashi.tepco.co.jp/pf/ja/pc/mypage/learn/comparison.page?ReqID=CsvDL&year=2021](https://www.kurashi.tepco.co.jp/pf/ja/pc/mypage/learn/comparison.page?ReqID=CsvDL&year=2021)
  - json [https://www.kurashi.tepco.co.jp/pf/ja/res/mypage/learn/comparison.page?\_ajax_request=1&year=2021](https://www.kurashi.tepco.co.jp/pf/ja/res/mypage/learn/comparison.page?_ajax_request=1&year=2021)

## Better API design?

TODO: Refine

- `/api/2021.json`
- `/api/2021.csv`
- `/api/2021-09.json`
- `/api/2021-09-29.json`
- `/api/2021/09/29/json`
- `/api/2021/09/29/csv`

## TEPCO API raw response

### Monthly

```js
{
  "status_code": "200",
  "data_day": null,
  "menu_type": "0",
  "smart_meter": "true",
  "contract_type": "0",
  "data_year": "2021",
  "data": [
    ...
    {
      "holiday_kwh": "-0",
      "metered_kwh": "-0",
      "temperature": null,
      "icon_id": "0017",
      "time": null,
      "rate": null,
      "daysummer_kwh": "-0",
      "weather": null,
      "peak_kwh": "-0",
      "summer_peak_kwh": "-0",
      "kwh": "110",
      "offpeak_kwh": "-0",
      "night_kwh": "-0",
      "tou_flag": "2",
      "fixedamount_kwh": "-0",
      "plan": "planL01-B00101",
      "yen": "4120",
      "daynighttime_kwh": "-0",
      "month": "4",
      "daytime_kwh": "-0",
      "weekday_kwh": "-0",
      "day": null,
      "nottou_kwh": "-0",
      "flat_kwh": null,
      "plan_name": "アクアエナジー１００"
    },
    ...
```

### Daily

```js
{
  "status_code": "200",
  "data_day": null,
  "menu_type": "0",
  "smart_meter": "true",
  "contract_type": "0",
  "data_year": "2021",
  "data": [
    {
      "holiday_kwh": "-0",
      "metered_kwh": "-0",
      "temperature": "20.9",
      "icon_id": "0017",
      "time": null,
      "rate": null,
      "daysummer_kwh": "-0",
      "weather": "雨時々止む",
      "peak_kwh": "-0",
      "summer_peak_kwh": "-0",
      "kwh": "5.2",
      "offpeak_kwh": "-0",
      "night_kwh": "-0",
      "tou_flag": null,
      "fixedamount_kwh": "-0",
      "plan": "planL01-B00101",
      "yen": "-0",
      "daynighttime_kwh": "-0",
      "month": "9",
      "daytime_kwh": "-0",
      "weekday_kwh": "-0",
      "day": "1",
      "nottou_kwh": "-0",
      "flat_kwh": null,
      "plan_name": "アクアエナジー１００"
    },
```

### Hourly (no data)

```js
{
  "status_code": "2",
  "data_day": "29",
  "menu_type": "0",
  "smart_meter": "true",
  "contract_type": "0",
  "data_year": "2021",
  "data": [],
  "data_month": "9",
  "display30min": "true",
  "plan_change": []
}
```

### Hourly (data existing)

```js
{
  "status_code": "200",
  "data_day": "28",
  "menu_type": "0",
  "smart_meter": "true",
  "contract_type": "0",
  "data_year": "2021",
  "data": [
    {
      "holiday_kwh": "-0",
      "metered_kwh": "-0",
      "temperature": null,
      "icon_id": "0017",
      "time": "00:30",
      "rate": null,
      "daysummer_kwh": "-0",
      "weather": null,
      "peak_kwh": "-0",
      "summer_peak_kwh": "-0",
      "kwh": "0.1",
      "offpeak_kwh": "-0",
      "night_kwh": "-0",
      "tou_flag": null,
      "fixedamount_kwh": "-0",
      "plan": "planL01-B00101",
      "yen": "-0",
      "daynighttime_kwh": "-0",
      "month": "9",
      "daytime_kwh": "-0",
      "weekday_kwh": "-0",
      "day": "28",
      "nottou_kwh": "-0",
      "flat_kwh": null,
      "plan_name": "アクアエナジー１００"
    },
```
