# Motivation
We are lazy! Let make it as easy as possible to config.

# Installation
```
npm install --save enhance-console-log
```

# Setup
Just import and call on your entry point
```javascript
const enhanceConsoleLog = require('enhance-console-log')
enhanceConsoleLog()
```

# Configurationn
```javascript
// Default configuration
enhanceConsoleLog({
    dateFormat: 'YYYY-MM-DD HH:mm:ss.SSS',
    separator: '\t---',
    levelColor: {
        'debug': '#a0a0a0', 
        'log': '#dbdbdb', 
        'info': '#55a6e8', 
        'warn': '#f7b737',
        'error': '#b21111', 
    },
    // disabled some log level
    disabledLevel: {
        warn: true,
        log: process.env.NODE_ENV === 'production'
    }
})
```

# Simple Usage
Just call following console log function, debug, log, info, warn and error
```javascript
console.debug('This is console.debug()')
console.log('This is console.log()')
console.info('This is console.info()')
console.warn('This is console.warn()')
console.error('This is console.error()')
```
You will get following log with color if your terminal support
```javascript
2019-03-09 00:57:48.741 DEBUG   --- This is console.debug()
2019-03-09 00:57:48.741 LOG     --- This is console.log()
2019-03-09 00:57:48.741 INFO    --- This is console.info()
2019-03-09 00:57:48.741 WARN    --- This is console.warn()
2019-03-09 00:57:48.741 ERROR   --- This is console.error()
```
# Helper Logging Function
We provide some logging helper patch directly to console object
```javascript
console.debugWithPrefix(prefix: string)
console.logWithPrefix(prefix: string)
console.infoWithPrefix(prefix: string)
console.warnWithPrefix(prefix: string)
console.errorWithPrefix(prefix: string)
```
Example
```javascript
const orderInfoLog = console.infoWithPrefix('order:111111')
const orderLog = console.logWithPrefix('order:111111')

orderInfoLog('created')
orderLog('trying to update')
orderInfoLog('updated')
```
You will get following log
```javascript
2019-03-09 00:57:48.742 INFO    --- [order:111111] created
2019-03-09 00:57:48.742 LOG     --- [order:111111] trying to update
2019-03-09 00:57:48.742 INFO    --- [order:111111] updated
```