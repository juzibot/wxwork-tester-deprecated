# wxwork-tester

We have launched a new puppet `wechaty-puppet-wxwork`. It is ready for testing.

Unlike the previous puppet version, wechaty-puppet-wxwork is a **WeChat Work solution**.

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
