## Merculet集成文档（JS-SDK）

# 一. 集成准备

## 1导入SDK

> 特别提示: 请直接使用此链接, 不要将此文件下载到您项目中, 否则, 我们在更新数据结构或API接口后有可能会导致SDK失效。


```HTML
<script src="https://static.merculet.cn/scripts/dist/MerculetSDK.min.js"></script>
```

## 1.1获取Merculet AppKey等信息

### 1.2.1后台获取merculet Appkey等信息

登录后台管理（[http://mb-saas.magicwindow.cn](http://mb-saas.magicwindow.cn)）。进入“产品管理”菜单，填写相应内容创建应用，并获取应用的
appkey、account_key、account_secret的值。

## 1.3.1 获取Token

基于上述三个数值，接入方需要调用Merculet的签发Token的接口。[查看获取用户凭证](http://mb-helpcenter.magicwindow.cn/doc/api)



# 二．基本功能集成（必加项）

## 2.1初始化SDK


```javascript
var sdk = new MerculetSDK()
```


初始化完成之后，需要向sdk设置token

```javascript
sdk.setToken({ token: token })
```


## 2.2自定义事件功能

自定义事件的注册（配置）包括事件id的注册和事件，id下参数信息的注册。


```javascript
sdk.sendEvent()

// 示例：

sdk.sendEvent([
  {
    action: "read", // 事件key
    action_params: { // 事件属性
      sp_word_count: "100", // 属性值
      sp_timestamp: 1523844119702  // 当前时间戳
    }
  },
  {
    action: "active", // 事件key
    action_params: { // 事件属性
      sp_timestamp: 1523844119702  // 当前时间戳
    }
  }
]);



```

# 三．测试与调试

## 3.1测试前的准备

* 确认TOKEN正确签发等

* 确认setToken完成

## 3.2测试流程

使用普通测试流程，请先在程序入口初始化MerculetSDK添加以下代码打开调试模式：

```javascript
var sdk = new MerculetSDK({debug:true})
```

打开调试模式后，您可以在控制台中查看您的数据是否成功发送到merculet服务器，以及集成过程中的出错原因等。

| Log的tag  | 用途    | 结果           |
| -------- | ----- | ------------ |
| SDKDebug | 其他log | 系统调试的一些其他log |

注意：请使用普通测试流程，您的测试数据会与用户的真实使用数据同时处理，从而导致一定的数据污染。
