# bar

## This is a website by vuepress

搞了几个小时，终于用vuepress搭建起一个静态资源站点，总结下，记录下那些走过的坑

官方文档：https://vuepress.docschina.org/

## 安装

官方提供全局安装和在已有项目中安装两种方式，我使用的是在已有项目中安装

若yarn无法正常安装，推荐使用`cnpm install -g yarn`的方式来安装

```
# 安装为本地依赖项
yarn add -D vuepress # 或 npm install -D vuepress

# 创建一个 docs 目录
mkdir docs
# 创建一个 markdown 文件
echo '# Hello VuePress' > docs/README.md
```

项目目录结构：

tree -| docs
tree -| docs -| .vuepress
tres -| docs -| .vuepress > config.js
tres -| docs -| .vuepress -| public
tres -| docs -| .vuepress -| public > hero.png
tres -| docs -| foo
tres -| docs -| foo > README.md
tres -| docs -| foo > one.md
tres -| docs -| foo > two.md
tres -| docs -| bar
tres -| docs -| bar > README.md
tres -| docs -| bar > three.md
tres -| docs -| bar > four.md

#### 运行命令

`yarn docs:dev # 或 npm run docs:dev`

`yarn docs:build # 或 npm run docs:build`

#### package.json

```
module.exports = {
    base: '/bar/',   // github项目目录
    title: 'VuePress',  
    description: 'on shit , this is a website by vuepress',
    themeConfig: {
        //头部导航
        nav: [
            { text: 'foo', link: '/foo/' },
            { text: 'bar', link: '/bar/' }
        ],
        //侧边栏
        sidebar: [
            '/',
            '/page-a',
            ['/page-b', 'Explicit link text']
        ]
    }
}
```

#### README.md

```
---
home: true
heroImage: /hero.png
actionText: 起步 →
actionLink: /guide/
features:
- title: 简明优先
  details: 对以 markdown 为中心的项目结构，做最简化的配置，帮助你专注于创作。
- title: Vue 驱动
  details: 享用 Vue + webpack 开发环境，在 markdown 中使用 Vue 组件，并通过 Vue 开发自定义主题。
- title: 性能高效
  details: VuePress 将每个页面生成为预渲染的静态 HTML，每个页面加载之后，然后作为单页面应用程序(SPA)运行。
footer: MIT Licensed | Copyright © 2018-present Evan You
---
```

#### 关于部署github

因为`yarn docs:build`命令执行后，静态目录重新生成，故而需要每次生成git提交。。。（后续再研究下）

目前的做法是，将github仓库git克隆到本地，添加到项目的静态资源目录，执行相关命令，提交（表示官方文档示例没看明白）

在通过`yarn docs:dev`启动本地服务时，遇到了更新不及时的情况，可能是不太稳定，所写并非所得，故而需要耐心等待会儿。。。 