
## Install
It requires NodeJS 8+.

Easy to install the package with command:
```
npm install --save tomoxjs
```

## APIs
You can refer to [TomoX API Document](https://apidocs.tomochain.com/#tomodex-apis) to know the APIs that will work with the SDK

## Use
You need to declare Relayer URL and your private key to unlock the wallet. You can create a private key at [https://wallet.tomochain.com](https://wallet.tomochain.com)
```javascript
const TomoX = require('tomoxjs')


const relayerUri = 'https://dex.tomochain.com'  // TomoChain Relayer URL
const pkey = '0x0' // your private key

const tomox = new TomoX(relayerUri, pkey)
```


### Create order
Before creating an order, make sure you have enough balance for the trade and fee.

```javascript
tomox.createOrder({
    baseToken:'0xBD8b2Fb871F97b2d5F0A1af3bF73619b09174B2A', // Base Token Address e.g BTC
    quoteToken: '0x0000000000000000000000000000000000000001', // Quote Token Address e.g TOMO
    price: '21207.02',
    amount: '0.004693386710283129'
}).then(data => {
        console.log(data)
    }).catch(e => {
        console.log(e)
    })
```

### Create many orders
It is the same as creating order, just need to input array of orders you need to create.

```javascript
tomox.createManyOrders([{
    baseToken:'0xBD8b2Fb871F97b2d5F0A1af3bF73619b09174B2A', // Base Token Address e.g BTC
    quoteToken: '0x0000000000000000000000000000000000000001', // Quote Token Address e.g TOMO
    price: '21207.02',
    amount: '0.004693386710283129'
}]).then(data => {
        console.log(data)
    }).catch(e => {
        console.log(e)
    })
```

### Cancel order
After creating an order, you can cancel it with order hash
```javascript
const orderHash = '0x0' // hash of order you want to cancel
tomox.cancelOrder(orderHash)
    .then(data => {
        console.log(data)
    }).catch(e => {
        console.log(e)
    })
```

### Get account balances
Get the current account balances
```javascript
tomox.getAccount()
    .then(data => {
        console.log(data)
    }).catch(e => {
        console.log(e)
    })
```
Get the specify account balances
```javascript
tomox.getAccount(address)
    .then(data => {
        console.log(data)
    }).catch(e => {
        console.log(e)
    })

