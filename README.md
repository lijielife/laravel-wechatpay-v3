# laravel-ultimatemusic

用于 Laravel 框架的爱听卓乐音乐组件

## 安装
不低于 Laravel 5.7

```shell
$ composer require friendsmore/laravel-wechatpay-v3:^1.0
```

## Laravel 配置方法

由于设置了 Laravel providers 自动加载，所以不需要额外操作。

## Lumen 配置方法

在 `bootstrap/app.php` 中增加：
```php
$app->register(LaravelWechatpayV3\ServiceProvider::class);
```

## 使用
```php
use LaravelWechatpayV3\Facade as WechatpayV3;

$wechatPay = WechatpayV3::app();

// 证书目录
$wechatPay->certificate->all($query, $options);

// 解析异步通知
$wechatPay->notify->parseResponse($response);

// 上传媒体文件
$wechatPay->media->upload($file, $options);

// 子商户入驻（申请）
$wechatPay->applyment->create($params, $options);

// 子商户入驻（查询）
$wechatPay->applyment->retrieve($id, $query, $options);

// 合单支付（app）
$wechatPay->combineTransaction->createByApp($params, $options);

// 合单支付（jsApi）
$wechatPay->combineTransaction->createByJsApi($params, $options);

// 合单支付查询
$wechatPay->combineTransaction->retrieveByOutTradeNo($outTradeNo, $query, $options); // 使用商户订单号

// 合单支付关闭
$wechatPay->combineTransaction->closeByOutTradeNo($outTradeNo, $query, $options); // 使用商户订单号

// 退款（发起）
$wechatPay->refund->create($params, $options);

// 退款（查询）
$wechatPay->refund->retrieveByOutRefundNo($id, $query, $options); // 使用商户退款单号
$wechatPay->refund->retrieve($id, $query, $options);  // 使用微信退款单号

// 分账（请求分账）
$wechatPay->profitSharingOrder->create($params, $options);

// 分账（查询分账）
$wechatPay->profitSharingOrder->retrieve($id, $query, $options);

// 分账（请求分账回退）
$wechatPay->profitSharingReturnOrder->create($params, $options);

// 分账（查询分账回退）
$wechatPay->profitSharingReturnOrder->retrieve($id, $query, $options);

// 分账（完结分账）
$wechatPay->profitSharingFinishOrder->create($params, $options);

// 提现（发起）
$wechatPay->withdraw->create($params, $options);

// 提现（查询）
$wechatPay->withdraw->retrieve($id, $query, $options);

// 查询余额
$wechatPay->balance->retrieve($subMerchantId, $query, $options);

// 申请交易账单
$wechatPay->bill->retrieveTradeBill($query, $options);

// 申请资金账单
$wechatPay->bill->retrieveFundFlowBill($query, $options);

// 账单文件下载
$wechatPay->bill->download($body); // $body 使用申请交易账单或申请资金账单接口返回的数据
```