---
// src/pages/about.astro
// 彻底不使用常规 Layout，实现纯净白卡片单页效果
---

<html lang="zh-CN">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>关于 - Xane</title>
    <style>
      :root {
        --primary-color: #3b82f6;
      }
      body {
        margin: 0;
        padding: 40px 20px;
        background-color: #f4f7f6; /* 淡淡的底色 */
        font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 100vh;
        box-sizing: border-box;
      }
      .card {
        background: #ffffff;
        border-radius: 24px;
        padding: 50px 40px;
        max-width: 800px;
        width: 100%;
        box-shadow: 0 4px 30px rgba(0, 0, 0, 0.02);
        position: relative;
        overflow: hidden;
      }
      /* 背景大艺术字 */
      .bg-text {
        position: absolute;
        font-size: 10rem;
        font-weight: 900;
        color: #f0f4f9;
        z-index: 1;
        letter-spacing: 4px;
        user-select: none;
        pointer-events: none;
      }
      .bg-about { top: -20px; left: 50%; transform: translateX(-50%); }
      .bg-tech { bottom: 120px; left: 50%; transform: translateX(-50%); font-size: 7.5rem; }

      .content-wrapper {
        position: relative;
        z-index: 2;
      }

      /* 头部布局 */
      .profile-section {
        display: flex;
        gap: 32px;
        align-items: flex-start;
        margin-top: 40px;
        margin-bottom: 32px;
      }
      .avatar-wrapper {
        position: relative;
      }
      .avatar {
        width: 150px;
        height: 150px;
        border-radius: 20px;
        object-fit: cover;
        border: 4px solid #4f86f7; /* 模仿图中的蓝色边框 */
      }
      .profile-info h1 {
        margin: 0 0 8px 0;
        font-size: 2.2rem;
        color: #1e293b;
        font-weight: 700;
      }
      .profile-info .subtitle {
        margin: 0 0 20px 0;
        font-size: 1.1rem;
        color: #64748b;
      }

      /* 按钮组 */
      .button-group {
        display: flex;
        gap: 10px;
        flex-wrap: wrap;
        margin-bottom: 24px;
      }
      .btn {
        display: inline-flex;
        align-items: center;
        gap: 6px;
        padding: 8px 16px;
        border: 1px solid #e2e8f0;
        border-radius: 10px;
        font-size: 0.95rem;
        color: #334155;
        text-decoration: none;
        background: #fff;
        transition: all 0.2s;
      }
      .btn:hover {
        background: #f8fafc;
        border-color: #cbd5e1;
      }

      /* 文本介绍 */
      .bio {
        font-size: 1rem;
        color: #334155;
        line-height: 1.7;
        margin-bottom: 48px;
      }

      /* 技术堆栈部分 */
      .section-title {
        font-size: 1.5rem;
        color: #0f172a;
        margin-bottom: 32px;
        font-weight: 700;
      }
      .tech-grid {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
        gap: 20px;
        margin-top: 80px; /* 给 TECH STACK 背景字留出空间 */
      }
      .tech-card {
        background: #fff;
        border-radius: 16px;
        padding: 24px;
        box-sizing: border-box;
        transition: transform 0.2s;
      }
      .tech-card-title {
        font-weight: 700;
        font-size: 1.1rem;
        margin-bottom: 4px;
        display: flex;
        align-items: center;
        gap: 8px;
      }
      .tech-card-sub {
        font-size: 0.85rem;
        color: #94a3b8;
        margin-bottom: 12px;
      }
      .tech-card p {
        font-size: 0.9rem;
        color: #475569;
        margin: 0;
        line-height: 1.6;
      }

      /* 精准匹配图中的卡片边框颜色 */
      .card-astro { border: 1px solid #f97316; }
      .card-fuwari { border: 1px solid #a855f7; }
      .card-cloudflare { border: 1px solid #3b82f6; }

      @media (max-width: 640px) {
        .profile-section { flex-direction: column; align-items: center; text-align: center; }
        .button-group { justify-content: center; }
        .bg-text { font-size: 5rem; }
        .bg-tech { font-size: 3.5rem; bottom: 220px; }
      }
    </style>
  </head>
  <body>

    <div class="card">
      <!-- 艺术背景字 -->
      <div class="bg-text bg-about">ABOUT</div>
      
      <div class="content-wrapper">
        <!-- 个人信息 -->
        <div class="profile-section">
          <div class="avatar-wrapper">
            <img src="https://img.imgla.net/free/6a2528ea6dc0e.jpg" alt="Avatar" class="avatar" />
          </div>
          <div class="profile-info">
            <h1>Xane</h1>
            <div class="subtitle">Android & Web Developer</div>
            
            <div class="button-group">
              <a href="https://github.com" target="_blank" class="btn">
                <svg height="18" width="18" viewBox="0 0 16 16"><path fill="currentColor" d="M8 0C3.58 0 0 3.58 0 8c0 3.54 2.29 6.53 5.47 7.59.4.07.55-.17.55-.38 0-.19-.01-.82-.01-1.49-2.01.37-2.53-.49-2.69-.94-.09-.23-.48-.94-.82-1.13-.28-.15-.68-.52-.01-.53.63-.01 1.08.58 1.23.82.72 1.21 1.87.87 2.33.66.07-.52.28-.87.51-1.07-1.78-.2-3.64-.89-3.64-3.95 0-.87.31-1.59.82-2.15-.08-.2-.36-1.02.08-2.12 0 0 .67-.21 2.2.82.64-.18 1.32-.27 2-.27.68 0 1.36.09 2 .27 1.53-1.04 2.2-.82 2.2-.82.44 1.1.16 1.92.08 2.12.51.56.82 1.27.82 2.15 0 3.07-1.87 3.75-3.65 3.95.29.25.54.73.54 1.48 0 1.07-.01 1.93-.01 2.2 0 .21.15.46.55.38A8.013 8.013 0 0016 8c0-4.42-3.58-8-8-8z"/></svg>
                GitHub
              </a>
              <a href="mailto:your-email@example.com" class="btn">✉️ Email</a>
            </div>
          </div>
        </div>

        <!-- 个人简介 -->
        <div class="bio">
          你好呀！我是 Xane，一名选科为物理、化学、地理的高中生。习惯在理性的课业之外折腾设备、编写独立应用。偏爱通透、具纸张质感的极简数字美学。
        </div>

        <!-- 技术信息标题 -->
        <div class="section-title">技术信息</div>
      </div>

      <!-- 艺术背景字 2 -->
      <div class="bg-text bg-tech">TECH STACK</div>

      <div class="content-wrapper">
        <!-- 技术卡片网格 -->
        <div class="tech-grid">
          <div class="tech-card card-astro">
            <div class="tech-card-title" style="color: #f97316;">🚀 Astro</div>
            <div class="tech-card-sub">构建框架</div>
            <p>Astro 是一个为构建快速、内容驱动的网站而优化的 JavaScript Web 框架。</p>
          </div>

          <div class="tech-card card-fuwari">
            <div class="tech-card-title" style="color: #a855f7;">🎨 Fuwari</div>
            <div class="tech-card-sub">博客主题</div>
            <p>Fuwari 是一个基于 Astro 开发的、兼具清爽视觉与流畅阅读体验的静态博客模板。</p>
          </div>

          <div class="tech-card card-cloudflare">
            <div class="tech-card-title" style="color: #3b82f6;">☁️ Cloudflare</div>
            <div class="tech-card-sub">托管服务</div>
            <p>本站部署于 Cloudflare 平台，为静态站点提供快速、安全且高可用的全球网络分发。</p>
          </div>
        </div>
      </div>

    </div>

  </body>
</html>