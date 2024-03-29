# Procon21-Backend-Summary

本ドキュメントでは、2021年度「U-22 プログラミングコンテスト」のHCB BackendAPIについてまとめている。


## DevideID
- 000001

## activity State
|   ID  | 動作  |
| ---- | ---- |
|1|  作業開始  | 
|2|  休憩開始  |
|3|  休憩終了 |
|4|  作業終了  |

## エンドポイント一覧
|   ID  |エンドポイント  |
| ---- | ---- |
|1|  /login  | 
|2|  /activity/regist  |
|3|  /activity/end  |
|4|  /sensor/{deviceID}  |
|5|  /activity/polling/{deviceID}  |


## エンドポイントと担っている処理について
|   ID  |  エンドポイント  | 処理  |
| ---- | ---- | ---- |
|1|  /login  |  ログイン認証  |
|2|  /activity/regist  |  作業開始、休憩開始・終了時間の記録  |
|3|  /activity/end  |  作業終了時間の記録、作業開始時間から経過した時間の算出  |
|4|  /sensor/{deviceID}  | 　作業開始前のデバイス選択時にデバイスの動作を確認  |
|5| /activity/sensor/data  |  作業時にデバイスから取得したデータを送る  |

## エンドポイントのリクエストとレスポンス
### 1 /login
- Method：POST
- Request

```
{
    "userID":"0001",
    "password":"0001"
}
```
- Response
```
{
  "errorMessage": ""
}
```
[エンドポイントの詳細について](https://github.com/Hokkaido-cheese-beef/Procon21-Backend-Login)

### 2  /activity/regist
- Method：POST
- Request
```
{
    "userID":"0001",
    "timestamp":1629625499,
    "status":3
}
```

- Response
```
{
  "Message": ""
}
or
{
  "Message": "request is wrong"
}
```
※サーバーエラーの時はステータスコードなどを返します。

[エンドポイントの詳細について](https://github.com/Hokkaido-cheese-beef/Procon2021RegistUserActivity)

### 3 /activity/end
- Method：POST
- Request
```
{
    "userID":"0001",
    "timestamp":1629629671,
    "status":1
}
```
```
{
  "workingTime": 14700
}

```
- Response

[エンドポイントの詳細について](https://github.com/Hokkaido-cheese-beef/Procon21-Backend-WorkingTime)

### 4 /sensor/{deviceID}
- Method：Get
- Request
エンドポイントの/sensorの後にユーザーが入力したdevideIDを指定

- Response
```
{
  "Message": "action"
}
or
{
  "Message": "not action"
}
```
他にもIDが正しくない場合などもメッセージを返却します。

[エンドポイントの詳細について](https://github.com/Hokkaido-cheese-beef/Procon21-Backend-CheckSensor)


### 5 /activity/polling/{deviceID}
- Method：GET
- Request 
エンドポイントの/pollingの後にユーザーが入力したdevideIDを指定
- Response
```
{
  "co2": 732,
  "temp": 26.74,
  "hum": 65.89,
  "message": "汗をかきやすい環境です！\n熱中症に気をつけましょう！"
}
```

[エンドポイントの詳細について]()
