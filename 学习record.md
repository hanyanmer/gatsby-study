# 简介
基于react的现代静态网页生成器。使用react组件来构建，然后编译为静态文件，这些文件可以部署到任何支持静态文件托管的服务器上。

主要特点：
React 驱动： Gatsby 使用 React 来构建网站。你可以使用 React 组件来创建页面和布局，借助 React 的强大功能来构建用户界面。

静态站点生成： Gatsby 会将 React 组件编译成静态 HTML、CSS 和 JavaScript 文件，这使得网站可以以更快的速度加载，同时也更容易进行缓存和部署。

数据源插件： Gatsby 提供了丰富的数据源插件，允许你从各种数据源中提取数据，包括文件系统、数据库、外部 API 等。

GraphQL 查询： Gatsby 使用 GraphQL 作为数据查询语言。你可以使用 GraphQL 查询语法来获取你所需要的数据，而 Gatsby 将确保只获取你页面渲染所需的数据。

插件生态系统： Gatsby 有一个强大的插件生态系统，可以通过插件来扩展和定制功能。这包括优化图像、SEO、分析等。

自动优化： Gatsby 自动进行了许多性能优化，包括图像优化、代码分割、懒加载等，以确保生成的网站具有最佳性能。

部署简单： 由于生成的网站是静态文件，因此可以轻松地部署到各种托管服务，如 Netlify、Vercel、GitHub Pages 等。

# 设置开发环境
([安装教程](https://www.gatsbyjs.cn/tutorial/part-zero/))
注意：安装的时候遇到一个问题， 使用yarn安装之后，找不到命令，只要npm的方式才能创建成功，该问题待寻找原因。



# 了解gatsby的构建模块
([构建模块](https://www.gatsbyjs.cn/tutorial/part-one/))
广义上来讲，组件是网站的构建模块。
## 页面组件

在src/pages/index.js这个组件，启动项目后如8000端口。可以通过http://localhost:8000 访问

在src/pages/*.js 中的react组件，在浏览器中都是一个页面。

定义一个src/pages/about.js 则可以在http://localhost:8000/about 访问该页面
## 子组件

上面是页面组件， 那么我们使用子组件，比如在about页面把当前页面划分不同的部分。


1. 新建src/components ，然后在这里组件中定义子组件如header.js
2. 把这个组件引入到about.js中 ，这里和react开发引入组件一样。

## 跳转到其他子页面
<Link to="/about">点击跳转到 httP://localhost:8000/about 页面</Link>

也可以使用a标签

## 布局组件
布局组件用于你要在多个页面上共享的网站公共部分。例如页眉，页脚的布局组件。
### gatsby插件
gatsby插件： 主要用于向gatsby网站添加功能的JavaScript包。
#### 安装和配置gatsby-plugin-typography
1. 安装
```shell
npm install --save gatsby-plugin-typography react-typography typography typography-theme-fairy-gates
```
注意： typography有很多依赖包，都要列举出来。
2. 配置 gatsby-config.js,在这里添加插件
```js
module.exports = {
  plugins: [
    {
      resolve: `gatsby-plugin-typography`,
      options: {
        pathToConfigModule: `src/utils/typography`,
      },
    },
  ],
}
```
3. typography需要一个配置文件，在src/utils/中添加一个typography.js文件，并修改内容
```js
import Typography from "typography"
import fairyGateTheme from "typography-theme-fairy-gates"

const typography = new Typography(fairyGateTheme)

export const { scale, rhythm, options } = typography
export default typography
```
4. 启动服务器
### 创建布局组件
1. src/components/layout.js
```js
import React from "react"

export default ({ children }) => (
  <div style={{ margin: `3rem auto`, maxWidth: 650, padding: `0 1rem` }}>
    {children}
  </div>
)
```
2. 将此布局引入到src/pages/index.js中
```js
import React from "react"
import Layout from "../components/layout"

export default () => (
  <Layout>
    <h1>Hi! I'm building a fake Gatsby site as part of a tutorial!</h1>
    <p>
      What do I like to do? Lots of course but definitely enjoy building
      websites.
    </p>
  </Layout>
)
```

已经生效
## 部署gatsby网站

## 样式引入
1. 我们可以把样式放在src/styles/global.css
2. 在gatsby-browser.js中引入
注意： gatsby-browser.js是gatsby自动扫描并使用的文件。

注意:以 .module.css结尾的文件为模块文件

通常使用postcss的tailwindcss插件

## 数据




