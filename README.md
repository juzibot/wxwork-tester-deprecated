# 最新消息

 [WorkPro](https://wechaty.js.org/2022/12/23/introducing-workpro-puppet/) 作为 WxWork 的继任者已经正式上线了！WxWork 现已废弃，请尽快转移到 WorkPro 上。

# wxwork-tester

`wechaty-puppet-wxwork` 已正式发布！ 这个 puppet 是一个企业微信而非个人微信的puppet，通过6行代码，你就可以运行你的企微机器人！ 通过下面方式可以获得token：
 
1. [注册](https://miaohui.juzibot.com/auth/register)
2. [购买](https://work.weixin.qq.com/kfid/kfcbfceaec6e8e30afe)

联系微信：juzibot

## Run

### Install

```
npm install wechaty
```

> 如果使用的是wechaty@1.x版本，需要增加环境变量配置: WECHATY_PUPPET_SERVICE_NO_TLS_INSECURE_CLIENT=true

### Example
```ts
import { Wechaty } from 'wechaty'
import { ScanStatus } from 'wechaty-puppet'
import QrcodeTerminal from 'qrcode-terminal';

const token = 'PUT_YOUR_TOKEN_HERE'

const bot = new Wechaty({
  puppet: 'wechaty-puppet-service',
  puppetOptions: {
    token,
  }
});

bot
  .on('scan', (qrcode, status) => {
    if (status === ScanStatus.Waiting) {
      QrcodeTerminal.generate(qrcode, {
        small: true
      })
    }
  })
  .on('login', async user => {
    console.log(`user: ${JSON.stringify(user)}`)
  })
  .on('message', async message => {
    console.log(`message: ${JSON.stringify(message)}`)
  })
  .start()
```

## Puppet Comparison

Puppet | donut | padplus | wxwork
:---|:---:|:---:| :---:
支持账号|个人微信|个人微信|企业微信
**<消息>**|  |  |  |
收发文本| ✅  | ✅  |✅
收发个人名片| ✅  |✅   |✅
收发图文链接| ✅  |✅   |✅
发送图片、文件| ✅  | ✅（对内容有大小限制，20M以下）  |✅
接收图片、文件| ✅  | ✅（对内容有大小限制，25M以下）  |✅
发送视频| ✅  | ✅   |✅
接收视频| ✅  | ✅   |✅
发送小程序| ✅  | ✅   |✅
接收动图| ❌  | ✅   |✅
发送动图| ✅  | ✅  |✅
接收语音消息| ✅  | ✅   |✅
发送语音消息| ❌  | ❌  |❌
转发文本| ✅  | ✅   |✅
转发图片| ✅  | ✅  |✅
转发图文链接| ✅  | ✅  |✅
转发音频| ✅ | ❌   |✅
转发视频| ✅  | ✅   |✅
转发文件| ✅  | ✅   |✅
转发动图| ❌  | ❌   |✅
转发小程序| ✅ | ✅   |✅
**<群组>**|   |    |
创建群聊|✅|✅ |✅
设置群公告|✅|✅|✅
获取群公告|❌|✅|❌
群二维码|❌|✅ |❌
拉人进群|✅|✅ |✅
踢人出群|✅|✅ |✅
退出群聊|✅|✅ |❌
改群名称|✅|✅ |✅
入群事件|✅|✅ |✅
离群事件|✅|✅ |✅
群名称变更事件|✅|✅|✅
@群成员|✅|✅|✅
群列表|✅|✅ |✅
群成员列表|✅|✅|✅
群详情|✅|✅|✅
**<联系人>**|  |   |
修改备注|✅|✅ |✅
添加好友|✅|✅|✅
自动通过好友|✅|✅|✅
好友列表|✅|✅ |✅
好友详情|✅|✅|✅
**<其他>**|  |   |
登录事件|✅|✅|✅
扫码状态|❌|✅|❌
登出事件|✅|✅|✅
主动退出登录|✅|✅|❌
依赖协议|Windows|iPad| Windows|
