# tdxquant
tdx quant


### 刷新行情缓存 - tq.refresh_cache()

~~~
'''
    刷新行情缓存 刷新后5分钟内取最新report和k线数据不会触发刷新
    force参数表示是否强制刷新 默认False
    market参数表示指定市场刷新
    'AG'表示A股 'HK'表示港股 'US'表示美股 'QH'表示期货  'QQ'表示期权  'ZZ'表示中证国证指数 'ZS' 表示沪深京指数
'''
refresh_cache = tq.refresh_cache()
print(refresh_cache)

~~~

output

~~~
TQ数据接口初始化成功，使用路径: d:\Thirdprogram\newtdxtqv772\PYPlugins\user\tdxdata_test_demo.py
{"ErrorId":"0","Msg":"Refresh Cache Success.","run_id":"2"}
~~~

###  获取分红送配数据 - tq.get_divid_factors

~~~
divid_factors = tq.get_divid_factors(
        stock_code='688318.SH',
        start_time='',
        end_time='')
print(divid_factors)
~~~

output

~~~
           Type  Bonus  AllotPrice  ShareBonus  Allotment
Date                                                     
2020-09-29    1    6.0         0.0         0.0        0.0
2021-05-27    1   10.0         0.0         0.0        0.0
2022-06-20    1   14.0         0.0         4.0        0.0
2023-06-13    1    5.0         0.0         4.0        0.0
2024-06-14    1    8.0         0.0         4.0        0.0
2024-10-18    1    1.1         0.0         0.0        0.0
2025-06-06    1    5.0         0.0         4.0        0.0
2026-06-05    1    3.8         0.0         4.0        0.0

~~~

###  获取市场快照数据 - tq.get_market_snapshot

~~~
'''
    获取市场快照数据,调用会触发客户端刷新数据，耗时过长请耐心等待
    总成交额为万位，其他无特殊说明均为个位
    曾用名：get_full_tick get_report_data
'''
tq.refresh_cache(force=True)
market_snapshot = tq.get_market_snapshot(stock_code = '300078.SZ', field_list=[])
print(market_snapshot)

print(json.dumps(market_snapshot, indent=4, ensure_ascii=False))

~~~

output

~~~
{
    "ErrorId": "0",
    "ItemNum": "2332",
    "LastClose": "2.87",
    "Open": "2.84",
    "Max": "2.96",
    "Min": "2.82",
    "Now": "2.83",
    "Volume": "289706",
    "NowVol": "1318",
    "Amount": "8362.57",
    "Inside": "160425",
    "Outside": "129281",
    "TickDiff": "0.00",
    "InOutFlag": "2",
    "Jjjz": "0.00",
    "Buyp": [
        "2.83",
        "0.00",
        "0.00",
        "0.00",
        "0.00"
    ],
    "Buyv": [
        "1633",
        "0",
        "0",
        "0",
        "0"
    ],
    "Sellp": [
        "2.85",
        "0.00",
        "0.00",
        "0.00",
        "0.00"
    ],
    "Sellv": [
        "1411",
        "0",
        "0",
        "0",
        "0"
    ],
    "UpHome": "0",
    "DownHome": "0",
    "Before5MinNow": "2.82",
    "Average": "2.89",
    "XsFlag": "2",
    "Zangsu": "0.35",
    "ZAFPre3": "2.54"
}

~~~





### 获取股票涨跌停数据 -  tq.get_zdt_data(()

~~~

'''
    获取股票涨跌停数据
'''
zdt_data = tq.get_zdt_data(stock_list=['002745.SZ','688318.SH'])
print(zdt_data)
print(json.dumps(zdt_data, indent=4, ensure_ascii=False))

~~~

output

~~~
{
    "002745.SZ": {
        "Code": ".SZ",
        "TimeNow": "0",
        "ZDTStatusNow": "0",
        "ZDTStatusOri": "0",
        "FirstTimeZT": "0",
        "FirstTimeDT": "0",
        "LastOpenTimeZT": "0",
        "LastOpenTimeDT": "0",
        "LastTimeZT": "0",
        "LastTimeDT": "0",
        "OpenTimesZT": "0",
        "OpenTimesDT": "0",
        "FDVolMaxZT": "0.00",
        "FDVolMaxDT": "0.00",
        "VolZT": "0.00"
    },
    "688318.SH": {
        "Code": ".SZ",
        "TimeNow": "0",
        "ZDTStatusNow": "0",
        "ZDTStatusOri": "0",
        "FirstTimeZT": "0",
        "FirstTimeDT": "0",
        "LastOpenTimeZT": "0",
        "LastOpenTimeDT": "0",
        "LastTimeZT": "0",
        "LastTimeDT": "0",
        "OpenTimesZT": "0",
        "OpenTimesDT": "0",
        "FDVolMaxZT": "0.00",
        "FDVolMaxDT": "0.00",
        "VolZT": "0.00"
    }
}
~~~
