---
title: "Hugo主题添加暗黑(夜间)模式，并自动切换"
date: 2023-01-19
description: '继续完善博客主题风格，折腾过程，备份记录留档。由于自己并不懂技术，折腾博客过程中，想实现或者解决某一想法或问题时，都需要通过搜索引擎查阅大量的资料，花大把时间，最终才能勉强得以解决或者继续无解。这就是折腾过程中的乐趣，特别是实现或解决成功的那个兴奋欣慰感～～'
image: images/article/dark.svg
---

继续完善博客主题风格，折腾过程，备份记录留档。由于自己已习惯把终端设备外观设置成自动切换浅色或深色模式，为了夜间浏览体验，博客应该支持暗黑(夜间)模式。

以hugo关键词搜索主题应该怎么适配，相关资料很少，尝试到绝望之际，换成了英文关键词，最终Atanas Yonkov的"<a href="https://yonkov.github.io/post/add-dark-mode-toggle-to-hugo/" target="_blank">Adding Dark Mode to Hugo</a>"拯救了自己，根据其教程，添加成功。虽不完美，但已实现，纠结两个问题：

1.暗黑模式下，点击链接加载都会白一下再变暗。<br />2.不会根据终端设备模式自动切换，需要手动点击。

尝试搜索解决，无果。之后发现WorkPlusFE's Blog的"<a href="https://fe-blog.workplus.io/dark-mode-guide-on-web" target="_blank">Dark Mode</a>"教程，又是一番折腾，最终完美解决。最简单直接方式：在hugo样式文件中（如：style.scss）添加

```css
@media (prefers-color-scheme: dark) {
/* 暗黑模式下css样式, 如: */
  body {
    background: #1A1718;
}
}
```

完善暗黑模式下的样式属性之后，终端设备在深色模式下会自动调用渲染主题暗黑模式下的样式表，反之浅色模式下就调用默认样式。

### 扩展

当然如果要做好暗黑模式，并不是简单的反黑白，需要不断尝试样式的各个配色方案，以寻求夜间浏览的实际体验。不过图片可以采用降低透明度的方式来缓解夜间过亮刺眼的问题：

```css
@media (prefers-color-scheme: dark) {
  img {
    filter: brightness(0.8) contrast(1.2);
  }
}
```

### 感悟

由于自己并不懂技术，折腾博客过程中，想实现或者解决某一想法或问题时，都需要通过搜索引擎查阅大量的资料，花大把时间，最终才能勉强得以解决或者继续无解。这就是折腾过程中的乐趣，特别是实现或解决成功的那个兴奋欣慰感～～