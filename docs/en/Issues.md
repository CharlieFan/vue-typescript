# Issues
Have quite a few compatible issues When update to vue-loader 13.x 和 webpack3.x. The existing issues are as follow:

### change vue file or style will trigger browser refreshing
This refresh operation is under build/dev-server.js
```js
// force page reload when html-webpack-plugin template changes
compiler.plugin('compilation', function (compilation) {
    compilation.plugin('html-webpack-plugin-after-emit', function (data, cb) {
        hotMiddleware.publish({ action: 'reload' })
        cb()
    })
})
```
Right now we comment this piece of code, so if anything is changed on html under build/tpl, you need to refresh manually.

### production mode does not extract styles into css file
When build production, styles in components are not extracted into css files. Now there is no solution for that.

>  If you have any solutions or ideas, please submit [issue](https://github.com/MMF-FE/vue-typescript/issues) or [PR](https://github.com/MMF-FE/vue-typescript/pulls)