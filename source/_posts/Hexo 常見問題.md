---
title: Hexo 一些常見問題
date: 2021-10-03 17:46:21
tags:
  - Hexo
  - Hexo Deploy
  - GitHub Pages
---

使用 Hexo 架設部落格，部署到 Github page 遇上 css 失效
需在 \_config.yml 新增設定
url: https://帳號.github.io/專案名稱/
root: /專案名稱/

```yml
# _config.yml
url: https://s0227373691.github.io/blog/
root: /blog/
```
