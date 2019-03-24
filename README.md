##KOA2
#安装
`yarn add koa`
```js
const Koa = require('koa')
const app = new Koa()

app.use(async (ctx, next) => {
  console.log(ctx.href)
  console.log(ctx.path)
  console.log(ctx.url)
  console.log(ctx.method)
  ctx.body = 'Hello World!'
})

app.listen(8080)
```
koa服务器可以运行了
整个Koa核心代码3行
```js
const app = new Koa()
app.use(middleware)
app.listen(3000)
```

#纯函数
  函数的返回结果只依赖于它的参数
  无副作用

#中间件
```js
const Koa = require('koa')
const logger = require('koa-logger')
const session =  require('koa-session')
const app = new Koa()

app.keys = ['Hello', 'World']

app.use(logger())
app.use(session(app))

app.use(ctx=> {
  if (ctx.path === '/favicon.ico') return
  if (ctx.path === '/') {
    let n = ctx.session.count || 0
    ctx.session.count = ++n
    ctx.body = n + '次'
  } else if (ctx.path === '/hi') {
    ctx.body = 'Hello World'
  } else {
    ctx.body = '404'
  }
})

app.listen(8080)
```
  
#Koa2与Koa1的对比

#Koa2与Express


