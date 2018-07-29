## 基础使用
> 1 cd project  &&  npm init  &&  创建dist 、src/index.js、example/test.html
> 2 npm install webpack webpack-cli --save-dev
> 3 package.json
>>"scripts": {
>>>"dev": "webpack --mode development",
>>>"build": "webpack --mode production"
>>},
>>"devDependencies": {
>>>"webpack": "^4.16.3",
>>>"webpack-cli": "^3.1.0"
>>}
> 4 npm run build 或 npm run dev

package.json
参考 3
webpack.config.js
module.exports = {
output: {
path: __dirname,
filename: './dist/main.js',
library: 'pass',
libraryTarget: 'umd'
}
}
src/index.js
module.exports = function(){
alert('函数调用成功');
}
example/test.html
<button id="btn">测度调用打包文件里的函数</button>
<script src="../dist/main.js"></script>
<script> document.getElementById('btn').onclick = function(){ pass() } </script>


## 使用ES6语法
.babelrc
{
"presets": ["env"]
}
webpack.config.js
module.exports = {
output: {
path: __dirname,
filename: './dist/main.js',
library: 'pass',
libraryTarget: 'umd'
}
module: {
rules: [
{
test: /\.js$/,
exclude: /node_modules/,
use: {
loader: "babel-loader"
}
}
]
}
}
