<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>我的个人博客</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Microsoft YaHei', sans-serif;
            transition: background-color 0.5s ease, color 0.3s ease;
        }
        
        :root {
            --primary-color: #3498db;
            --secondary-color: #2c3e50;
            --text-color: #333;
            --light-bg: rgba(255, 255, 255, 0.9);
            --card-bg: rgba(255, 255, 255, 0.95);
            --shadow: 0 8px 20px rgba(0, 0, 0, 0.1);
            --border-radius: 12px;
        }
        
        body {
            background-color: #f5f7fa;
            background-image: url('https://images.unsplash.com/photo-1519681393784-d120267933ba?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');
            background-size: cover;
            background-attachment: fixed;
            background-position: center;
            color: var(--text-color);
            min-height: 100vh;
            line-height: 1.6;
        }
        
        .container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        /* 头部样式 */
        header {
            background-color: var(--light-bg);
            backdrop-filter: blur(10px);
            box-shadow: var(--shadow);
            padding: 20px 0;
            position: sticky;
            top: 0;
            z-index: 100;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 28px;
            font-weight: 700;
            color: var(--primary-color);
            text-decoration: none;
        }
        
        .logo span {
            color: var(--secondary-color);
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 30px;
        }
        
        nav ul li a {
            text-decoration: none;
            color: var(--secondary-color);
            font-weight: 600;
            font-size: 16px;
            padding: 8px 12px;
            border-radius: 6px;
        }
        
        nav ul li a:hover, nav ul li a.active {
            background-color: var(--primary-color);
            color: white;
        }
        
        /* 主要内容区域 */
        main {
            display: flex;
            flex-wrap: wrap;
            margin: 40px 0;
            gap: 30px;
        }
        
        /* 博客文章区域 */
        .blog-posts {
            flex: 3;
            min-width: 300px;
        }
        
        .blog-card {
            background-color: var(--card-bg);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            padding: 30px;
            margin-bottom: 30px;
            transition: transform 0.3s ease;
        }
        
        .blog-card:hover {
            transform: translateY(-5px);
        }
        
        .blog-card h2 {
            color: var(--secondary-color);
            margin-bottom: 15px;
            font-size: 24px;
        }
        
        .blog-meta {
            display: flex;
            align-items: center;
            color: #777;
            font-size: 14px;
            margin-bottom: 20px;
        }
        
        .blog-meta span {
            margin-right: 20px;
        }
        
        .blog-meta i {
            margin-right: 5px;
            color: var(--primary-color);
        }
        
        .excerpt {
            color: #555;
            margin-bottom: 20px;
            line-height: 1.8;
        }
        
        .read-more {
            display: inline-block;
            background-color: var(--primary-color);
            color: white;
            text-decoration: none;
            padding: 10px 20px;
            border-radius: 6px;
            font-weight: 600;
        }
        
        .read-more:hover {
            background-color: var(--secondary-color);
        }
        
        /* 侧边栏 */
        .sidebar {
            flex: 1;
            min-width: 280px;
        }
        
        .sidebar-widget {
            background-color: var(--card-bg);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            padding: 25px;
            margin-bottom: 30px;
        }
        
        .sidebar-widget h3 {
            color: var(--secondary-color);
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--primary-color);
        }
        
        .about-widget p {
            margin-bottom: 15px;
        }
        
        .social-links {
            display: flex;
            justify-content: space-around;
            margin-top: 20px;
        }
        
        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background-color: var(--primary-color);
            color: white;
            border-radius: 50%;
            text-decoration: none;
            transition: all 0.3s ease;
        }
        
        .social-links a:hover {
            background-color: var(--secondary-color);
            transform: scale(1.1);
        }
        
        .recent-posts li {
            margin-bottom: 15px;
            padding-bottom: 15px;
            border-bottom: 1px solid #eee;
            list-style: none;
        }
        
        .recent-posts li:last-child {
            border-bottom: none;
        }
        
        .recent-posts a {
            text-decoration: none;
            color: var(--secondary-color);
            font-weight: 600;
        }
        
        .recent-posts a:hover {
            color: var(--primary-color);
        }
        
        .recent-posts .post-date {
            font-size: 13px;
            color: #777;
            display: block;
            margin-top: 5px;
        }
        
        /* 自定义背景面板 */
        .customize-panel {
            background-color: var(--card-bg);
            border-radius: var(--border-radius);
            box-shadow: var(--shadow);
            padding: 25px;
            margin-bottom: 30px;
        }
        
        .customize-header {
            display: flex;
            justify-content: space-between;
            align-items: center;
            margin-bottom: 20px;
        }
        
        .customize-header h3 {
            color: var(--secondary-color);
            margin-bottom: 0;
            padding-bottom: 0;
            border-bottom: none;
        }
        
        .toggle-customize {
            background-color: var(--primary-color);
            color: white;
            border: none;
            border-radius: 6px;
            padding: 8px 15px;
            cursor: pointer;
            font-weight: 600;
        }
        
        .customize-options {
            display: block;
        }
        
        .customize-group {
            margin-bottom: 20px;
        }
        
        .customize-group label {
            display: block;
            margin-bottom: 8px;
            font-weight: 600;
            color: var(--secondary-color);
        }
        
        .color-picker {
            display: flex;
            gap: 10px;
            flex-wrap: wrap;
        }
        
        .color-option {
            width: 30px;
            height: 30px;
            border-radius: 50%;
            cursor: pointer;
            border: 2px solid transparent;
            transition: transform 0.2s;
        }
        
        .color-option:hover, .color-option.active {
            transform: scale(1.1);
            border-color: white;
        }
        
        .image-options {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 10px;
        }
        
        .image-option {
            height: 80px;
            border-radius: 8px;
            cursor: pointer;
            background-size: cover;
            background-position: center;
            border: 2px solid transparent;
            transition: all 0.3s ease;
        }
        
        .image-option:hover, .image-option.active {
            border-color: var(--primary-color);
            transform: scale(1.03);
        }
        
        .customize-actions {
            display: flex;
            gap: 10px;
            margin-top: 20px;
        }
        
        .customize-actions button {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        #apply-bg {
            background-color: var(--primary-color);
            color: white;
        }
        
        #reset-bg {
            background-color: #f0f0f0;
            color: var(--secondary-color);
        }
        
        /* 页脚 */
        footer {
            background-color: var(--light-bg);
            backdrop-filter: blur(10px);
            padding: 30px 0;
            text-align: center;
            margin-top: 40px;
            box-shadow: 0 -5px 15px rgba(0, 0, 0, 0.05);
        }
        
        .footer-content {
            display: flex;
            flex-direction: column;
            align-items: center;
        }
        
        .footer-logo {
            font-size: 22px;
            font-weight: 700;
            color: var(--primary-color);
            margin-bottom: 15px;
        }
        
        .copyright {
            color: #666;
            font-size: 14px;
        }
        
        /* 响应式设计 */
        @media (max-width: 768px) {
            .header-content {
                flex-direction: column;
                text-align: center;
            }
            
            nav ul {
                margin-top: 20px;
                justify-content: center;
            }
            
            nav ul li {
                margin: 0 10px;
            }
            
            .customize-options {
                grid-template-columns: 1fr;
            }
            
            .image-options {
                grid-template-columns: 1fr;
            }
        }
        
        /* 夜间模式样式 */
        body.dark-mode {
            --text-color: #f0f0f0;
            --light-bg: rgba(30, 30, 40, 0.9);
            --card-bg: rgba(40, 40, 50, 0.95);
            --secondary-color: #ddd;
        }
        
        body.dark-mode .blog-card,
        body.dark-mode .sidebar-widget,
        body.dark-mode .customize-panel {
            box-shadow: 0 8px 20px rgba(0, 0, 0, 0.3);
        }
        
        /* 背景图片覆盖层 */
        .bg-overlay {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            z-index: -1;
            background-color: rgba(0, 0, 0, 0.3);
        }
    </style>
</head>
<body>
    <!-- 背景覆盖层 -->
    <div class="bg-overlay"></div>
    
    <header>
        <div class="container header-content">
            <a href="#" class="logo">个人<span>博客</span></a>
            <nav>
                <ul>
                    <li><a href="#" class="active">首页</a></li>
                    <li><a href="#">文章</a></li>
                    <li><a href="#">分类</a></li>
                    <li><a href="#">关于</a></li>
                    <li><a href="#">联系</a></li>
                </ul>
            </nav>
        </div>
    </header>
    
    <div class="container">
        <main>
            <section class="blog-posts">
                <article class="blog-card">
                    <h2>探索人工智能的未来发展</h2>
                    <div class="blog-meta">
                        <span><i class="far fa-calendar"></i> 2026年2月15日</span>
                        <span><i class="far fa-user"></i> 作者：元宝</span>
                        <span><i class="far fa-folder"></i> 科技</span>
                    </div>
                    <p class="excerpt">人工智能正在以前所未有的速度改变我们的生活和工作方式。从机器学习到自然语言处理，AI技术正渗透到各个领域。本文将探讨AI未来五年的发展趋势，以及它如何继续塑造我们的世界...</p>
                    <a href="#" class="read-more">阅读全文</a>
                </article>
                
                <article class="blog-card">
                    <h2>如何打造高效的个人知识管理系统</h2>
                    <div class="blog-meta">
                        <span><i class="far fa-calendar"></i> 2026年2月10日</span>
                        <span><i class="far fa-user"></i> 作者：元宝</span>
                        <span><i class="far fa-folder"></i> 效率</span>
                    </div>
                    <p class="excerpt">在信息爆炸的时代，建立一个有效的个人知识管理系统至关重要。本文将分享我多年来总结的知识管理方法，包括工具选择、信息分类、笔记技巧和定期回顾等实用策略...</p>
                    <a href="#" class="read-more">阅读全文</a>
                </article>
                
                <article class="blog-card">
                    <h2>2026年网页设计趋势分析</h2>
                    <div class="blog-meta">
                        <span><i class="far fa-calendar"></i> 2026年2月5日</span>
                        <span><i class="far fa-user"></i> 作者：元宝</span>
                        <span><i class="far fa-folder"></i> 设计</span>
                    </div>
                    <p class="excerpt">随着技术的不断发展，网页设计也在持续演进。从沉浸式体验到人工智能驱动的个性化设计，2026年的网页设计将更加注重用户体验和可访问性。本文探讨了今年值得关注的网页设计趋势...</p>
                    <a href="#" class="read-more">阅读全文</a>
                </article>
            </section>
            
            <aside class="sidebar">
                <div class="sidebar-widget about-widget">
                    <h3>关于博主</h3>
                    <p>你好，我是元宝，一名对技术和设计充满热情的全栈开发者。这个博客是我分享学习心得和生活感悟的地方。</p>
                    <p>我相信技术应该服务于人，致力于创造美观、实用且易用的数字产品。</p>
                    <div class="social-links">
                        <a href="#"><i class="fab fa-github"></i></a>
                        <a href="#"><i class="fab fa-twitter"></i></a>
                        <a href="#"><i class="fab fa-linkedin-in"></i></a>
                        <a href="#"><i class="fab fa-instagram"></i></a>
                    </div>
                </div>
                
                <div class="customize-panel">
                    <div class="customize-header">
                        <h3>自定义背景</h3>
                        <button class="toggle-customize" id="toggleCustomize">展开选项</button>
                    </div>
                    
                    <div class="customize-options" id="customizeOptions">
                        <div class="customize-group">
                            <label>背景颜色</label>
                            <div class="color-picker">
                                <div class="color-option active" style="background-color: #f5f7fa;" data-color="#f5f7fa"></div>
                                <div class="color-option" style="background-color: #e8f5e9;" data-color="#e8f5e9"></div>
                                <div class="color-option" style="background-color: #fff3e0;" data-color="#fff3e0"></div>
                                <div class="color-option" style="background-color: #fce4ec;" data-color="#fce4ec"></div>
                                <div class="color-option" style="background-color: #e8eaf6;" data-color="#e8eaf6"></div>
                                <div class="color-option" style="background-color: #263238;" data-color="#263238"></div>
                            </div>
                        </div>
                        
                        <div class="customize-group">
                            <label>背景图片</label>
                            <div class="image-options">
                                <div class="image-option active" style="background-image: url('https://images.unsplash.com/photo-1519681393784-d120267933ba?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');" data-image="https://images.unsplash.com/photo-1519681393784-d120267933ba?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80"></div>
                                <div class="image-option" style="background-image: url('https://images.unsplash.com/photo-1506905925346-21bda4d32df4?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');" data-image="https://images.unsplash.com/photo-1506905925346-21bda4d32df4?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80"></div>
                                <div class="image-option" style="background-image: url('https://images.unsplash.com/photo-1518837695005-2083093ee35b?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');" data-image="https://images.unsplash.com/photo-1518837695005-2083093ee35b?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80"></div>
                                <div class="image-option" style="background-image: url('https://images.unsplash.com/photo-1506744038136-46273834b3fb?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80');" data-image="https://images.unsplash.com/photo-1506744038136-46273834b3fb?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80"></div>
                            </div>
                        </div>
                        
                        <div class="customize-group">
                            <label>上传自定义图片 (输入URL)</label>
                            <input type="text" id="customImageUrl" placeholder="https://example.com/image.jpg" style="width: 100%; padding: 10px; border: 1px solid #ddd; border-radius: 6px; margin-top: 5px;">
                        </div>
                        
                        <div class="customize-actions">
                            <button id="apply-bg">应用背景</button>
                            <button id="reset-bg">恢复默认</button>
                        </div>
                    </div>
                </div>
                
                <div class="sidebar-widget">
                    <h3>最近文章</h3>
                    <ul class="recent-posts">
                        <li>
                            <a href="#">探索人工智能的未来发展</a>
                            <span class="post-date">2026年2月15日</span>
                        </li>
                        <li>
                            <a href="#">如何打造高效的个人知识管理系统</a>
                            <span class="post-date">2026年2月10日</span>
                        </li>
                        <li>
                            <a href="#">2026年网页设计趋势分析</a>
                            <span class="post-date">2026年2月5日</span>
                        </li>
                        <li>
                            <a href="#">JavaScript ES2026 新特性预览</a>
                            <span class="post-date">2026年1月28日</span>
                        </li>
                        <li>
                            <a href="#">如何保持学习动力：我的经验分享</a>
                            <span class="post-date">2026年1月20日</span>
                        </li>
                    </ul>
                </div>
            </aside>
        </main>
    </div>
    
    <footer>
        <div class="container footer-content">
            <div class="footer-logo">个人博客</div>
            <p class="copyright">© 2026 个人博客 - 由元宝创建 | 保留所有权利</p>
        </div>
    </footer>

    <script>
        // 自定义背景功能
        document.addEventListener('DOMContentLoaded', function() {
            const toggleBtn = document.getElementById('toggleCustomize');
            const customizeOptions = document.getElementById('customizeOptions');
            const colorOptions = document.querySelectorAll('.color-option');
            const imageOptions = document.querySelectorAll('.image-option');
            const applyBtn = document.getElementById('apply-bg');
            const resetBtn = document.getElementById('reset-bg');
            const customImageUrl = document.getElementById('customImageUrl');
            const bgOverlay = document.querySelector('.bg-overlay');
            
            let selectedColor = '#f5f7fa';
            let selectedImage = 'https://images.unsplash.com/photo-1519681393784-d120267933ba?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80';
            let isImageMode = true;
            
            // 切换自定义面板
            toggleBtn.addEventListener('click', function() {
                if (customizeOptions.style.display === 'none' || customizeOptions.style.display === '') {
                    customizeOptions.style.display = 'block';
                    toggleBtn.textContent = '收起选项';
                } else {
                    customizeOptions.style.display = 'none';
                    toggleBtn.textContent = '展开选项';
                }
            });
            
            // 选择颜色
            colorOptions.forEach(option => {
                option.addEventListener('click', function() {
                    colorOptions.forEach(opt => opt.classList.remove('active'));
                    this.classList.add('active');
                    selectedColor = this.getAttribute('data-color');
                    isImageMode = false;
                    
                    // 移除图片选项的激活状态
                    imageOptions.forEach(opt => opt.classList.remove('active'));
                });
            });
            
            // 选择图片
            imageOptions.forEach(option => {
                option.addEventListener('click', function() {
                    imageOptions.forEach(opt => opt.classList.remove('active'));
                    this.classList.add('active');
                    selectedImage = this.getAttribute('data-image');
                    isImageMode = true;
                    
                    // 移除颜色选项的激活状态
                    colorOptions.forEach(opt => opt.classList.remove('active'));
                });
            });
            
            // 应用背景
            applyBtn.addEventListener('click', function() {
                // 检查是否有自定义URL
                if (customImageUrl.value.trim() !== '') {
                    selectedImage = customImageUrl.value.trim();
                    isImageMode = true;
                }
                
                if (isImageMode) {
                    document.body.style.backgroundImage = `url('${selectedImage}')`;
                    document.body.style.backgroundColor = '';
                    
                    // 确保背景图片显示正确
                    document.body.style.backgroundSize = 'cover';
                    document.body.style.backgroundAttachment = 'fixed';
                    document.body.style.backgroundPosition = 'center';
                } else {
                    document.body.style.backgroundColor = selectedColor;
                    document.body.style.backgroundImage = 'none';
                }
                
                // 根据背景调整覆盖层
                if (selectedColor === '#263238' || !isImageMode && parseInt(selectedColor.replace('#', ''), 16) < 0x888888) {
                    bgOverlay.style.backgroundColor = 'rgba(0, 0, 0, 0.1)';
                } else {
                    bgOverlay.style.backgroundColor = 'rgba(0, 0, 0, 0.3)';
                }
                
                // 显示成功消息
                showMessage('背景已更新！');
            });
            
            // 重置背景
            resetBtn.addEventListener('click', function() {
                document.body.style.backgroundImage = 'url("https://images.unsplash.com/photo-1519681393784-d120267933ba?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80")';
                document.body.style.backgroundColor = '';
                document.body.style.backgroundSize = 'cover';
                document.body.style.backgroundAttachment = 'fixed';
                document.body.style.backgroundPosition = 'center';
                
                // 重置选项
                colorOptions.forEach(opt => opt.classList.remove('active'));
                colorOptions[0].classList.add('active');
                
                imageOptions.forEach(opt => opt.classList.remove('active'));
                imageOptions[0].classList.add('active');
                
                customImageUrl.value = '';
                selectedColor = '#f5f7fa';
                selectedImage = 'https://images.unsplash.com/photo-1519681393784-d120267933ba?ixlib=rb-4.0.3&auto=format&fit=crop&w=1920&q=80';
                isImageMode = true;
                bgOverlay.style.backgroundColor = 'rgba(0, 0, 0, 0.3)';
                
                // 显示成功消息
                showMessage('背景已恢复默认！');
            });
            
            // 显示临时消息
            function showMessage(text) {
                const message = document.createElement('div');
                message.textContent = text;
                message.style.cssText = `
                    position: fixed;
                    top: 100px;
                    right: 20px;
                    background-color: var(--primary-color);
                    color: white;
                    padding: 15px 25px;
                    border-radius: 6px;
                    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
                    z-index: 1000;
                    font-weight: 600;
                    animation: fadeInOut 3s ease-in-out;
                `;
                
                document.body.appendChild(message);
                
                // 添加动画
                const style = document.createElement('style');
                style.textContent = `
                    @keyframes fadeInOut {
                        0% { opacity: 0; transform: translateY(-20px); }
                        10% { opacity: 1; transform: translateY(0); }
                        90% { opacity: 1; transform: translateY(0); }
                        100% { opacity: 0; transform: translateY(-20px); }
                    }
                `;
                document.head.appendChild(style);
                
                // 3秒后移除消息
                setTimeout(() => {
                    message.remove();
                    style.remove();
                }, 3000);
            }
            
            // 初始化：默认展开自定义面板
            customizeOptions.style.display = 'block';
            toggleBtn.textContent = '收起选项';
        });
    </script>
</body>
</html>
