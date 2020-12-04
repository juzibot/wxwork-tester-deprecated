# wxwork-tester

We have launched a new puppet `wechaty-puppet-wxwork`. It is ready for testing.

Unlike the previous puppet version, wechaty-puppet-wxwork is a **WeChat Work solution**.

Get Token: 
- [Register](https://qiwei.juzibot.com/user/login?isWechaty=true)
- [Buy Token](https://qiwei.juzibot.com/corpPremium/wechaty)

We provider WeChat Work Solution for free if you buy wxwork token!

## Run

### Install

> Only need to install wechaty

```
npm install wechaty@next
```

### Example
```ts
import { Wechaty } from 'wechaty'
import { ScanStatus } from 'wechaty-puppet'
import QrcodeTerminal from 'qrcode-terminal';

const token = 'PUT_YOUR_TOKEN_HERE'

const bot = new Wechaty({
  puppet: 'wechaty-puppet-hostie',
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
