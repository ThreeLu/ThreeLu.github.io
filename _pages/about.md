---
# 首页核心配置（保留侧边栏+基础布局）
layout: home
author_profile: true  # 关键：显示侧边栏（包含头像、联系方式等）
permalink: /          # 强制作为首页
title: "路宇轩的个人网站"
breadcrumbs: false    # 隐藏面包屑，保持页面简洁
---

<!-- 欢迎语头部 -->
<div style="padding: 1.5rem 0; margin-bottom: 2rem; border-bottom: 1px solid #eee;">
  <h1 style="margin: 0; color: #2c3e50;">欢迎来到我的个人网站</h1>
  <p style="margin: 0.8rem 0; font-size: 1.1rem; color: #666;">记录学习、科研与生活的点滴</p>
</div>

<!-- 核心介绍内容 -->
<div style="max-width: 850px; margin: 0 auto; line-height: 1.8;">
  ## 🌟 网站简介
  这里是我科研生活的记录平台，主要用于分享学习科研过程中的积累，以及记录生活中的日常。无论你是同学、老师，还是对图论、组合数学感兴趣的朋友，都能在这里找到相关的内容。

  ## 📚 网站内容说明
  本网站主要包含以下几个板块，方便你快速了解和浏览：
  - **读书笔记&讲义**：整理我在日常学习中的学习笔记，以及参与学术讨论班时的讲义资料，涵盖核心知识点、解题思路与研究方法；
  - **讨论班**：发布我主讲的图论讨论班的相关信息，包括最新讨论主题、时间、地点以及需要提前准备的内容；
  - **生活记录**：分享日常学习之外的生活点滴，比如科研之余的兴趣爱好、校园生活、外出交流等；
  - **关于我**：分享我的经历以及爱好。
</div>

<!-- 简单响应式样式优化（适配手机端） -->
<style>
@media (max-width: 768px) {
  div {
    padding: 0 1rem !important;
  }
  h1 {
    font-size: 1.8rem !important;
  }
}
</style>
