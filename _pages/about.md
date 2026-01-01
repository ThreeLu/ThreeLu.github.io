---
permalink: /
title: "我的学术网站"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

# 欢迎来到我的个人网站

  ## 📖 最新读书笔记（共 {{ site.publications | where: "category", "books" | size }} 篇）
  {% assign latest_books = site.publications | where: "category", "books" | sort: 'date' | reverse | slice: 0, 2 %}
  {% if latest_books.size > 0 %}
    <div style="margin-bottom: 2rem;">
      <ul style="list-style: none; padding: 0; border-left: 3px solid #3498db;">
        {% for note in latest_books %}
          <li style="padding: 1rem; margin-bottom: 1rem; background: #f8f9fa; border-radius: 4px;">
            <a href="{{ note.url }}" style="font-weight: bold; color: #2c3e50; font-size: 1.1rem; text-decoration: none;">
              {{ note.title }}
            </a>
            <p style="margin: 0.5rem 0; color: #666; font-size: 0.95rem;">
              <span style="color: #999;">发布时间：{{ note.date | date: "%Y-%m-%d" }}</span>
            </p>
            <p style="margin: 0; color: #555; font-size: 0.95rem;">
              {{ note.excerpt | strip_html | truncate: 120 }}
            </p>
          </li>
        {% endfor %}
      </ul>
    </div>
  {% else %}
    <p style="color: #666; padding: 1rem; background: #f8f9fa; border-radius: 4px;">暂未发布读书笔记，敬请期待～</p>
  {% endif %}

  ## 📝 最新讨论班讲义（共 {{ site.publications | where: "category", "manuscripts" | size }} 篇）
  {% assign latest_manuscripts = site.publications | where: "category", "manuscripts" | sort: 'date' | reverse | slice: 0, 2 %}
  {% if latest_manuscripts.size > 0 %}
    <div style="margin-bottom: 2rem;">
      <ul style="list-style: none; padding: 0; border-left: 3px solid #e74c3c;">
        {% for note in latest_manuscripts %}
          <li style="padding: 1rem; margin-bottom: 1rem; background: #f8f9fa; border-radius: 4px;">
            <a href="{{ note.url }}" style="font-weight: bold; color: #2c3e50; font-size: 1.1rem; text-decoration: none;">
              {{ note.title }}
            </a>
            <p style="margin: 0.5rem 0; color: #666; font-size: 0.95rem;">
              <span style="color: #999;">发布时间：{{ note.date | date: "%Y-%m-%d" }}</span>
            </p>
            <p style="margin: 0; color: #555; font-size: 0.95rem;">
              {{ note.excerpt | strip_html | truncate: 120 }}
            </p>
          </li>
        {% endfor %}
      </ul>
    </div>
  {% else %}
    <p style="color: #666; padding: 1rem; background: #f8f9fa; border-radius: 4px;">暂未发布讨论班讲义，敬请期待～</p>
  {% endif %}

  <!-- 查看全部链接 -->
  <div style="text-align: center; margin: 3rem 0;">
    <a href="/publications/" style="padding: 0.8rem 2rem; background: #2c3e50; color: white; text-decoration: none; border-radius: 4px; font-size: 1rem;">
      查看全部笔记/讲义
    </a>
  </div>
</div>


<!-- 简单样式优化（适配不同屏幕） -->
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
