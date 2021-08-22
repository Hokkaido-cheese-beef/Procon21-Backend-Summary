# Procon21-Backend-Summary

以前の話し合いのドキュメント
https://docs.google.com/document/d/12Cy2V0xDp_GIkE8NlG-ynWVhyAjLX8ntOmhdAwMk--A/edit?usp=sharing


本ドキュメントでは、2021年度「U-22 プログラミングコンテスト」のHCB BackendAPIについてまとめている。

## URL
https://yz05f6od8e.execute-api.ap-northeast-1.amazonaws.com/procon/

## エンドポイント一覧
|   ID  |エンドポイント  |
| ---- | ---- |
|1|  /login  | 
|2|  /activity/regist  |
|3|  /activity/end  |
|4|  /sensor/{deviceID}  |
|5|  /sensor/data  |


## エンドポイントと担っている処理について
|   ID  |  エンドポイント  | 処理  |
| ---- | ---- | ---- |
|1|  /login  |  ログイン認証  |
|2|  /activity/regist  |  作業開始、休憩開始・終了時間の記録  |
|3|  /activity/end  |  作業終了時間の記録、作業開始時間から経過した時間の算出  |
|4|  /sensor/{deviceID}  | 　作業開始前のデバイス選択時にデバイスの動作を確認  |
|5| /sensor/data  |  作業時にデバイスから取得したデータを送る  |

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


### 5 /sensor/data
- Method：GET
- Request

- Response

[エンドポイントの詳細について]()
