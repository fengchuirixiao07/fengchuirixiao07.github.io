<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>风吹日晓的个人博客</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Segoe UI', 'Microsoft YaHei', sans-serif;
        }
        
        body {
            background-color: #f5f7fa;
            color: #333;
            line-height: 1.6;
            display: flex;
            min-height: 100vh;
        }
        
        /* 左侧导览栏 - 拉长版本 */
        .sidebar {
            width: 320px; /* 增加宽度 */
            background-color: #f8f9fa;
            border-right: 1px solid #eaeaea;
            padding: 50px 0; /* 增加上下内边距 */
            position: fixed;
            top: 0;
            left: 0;
            bottom: 0;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
        }
        
        .blog-info {
            padding: 0 35px; /* 增加左右内边距 */
            margin-bottom: 60px; /* 增加下边距 */
            text-align: center;
        }
        
        .blog-title {
            font-size: 32px; /* 增加字体大小 */
            font-weight: 700;
            color: #2c3e50;
            margin-bottom: 15px;
            letter-spacing: 1px;
        }
        
        .blog-subtitle {
            font-size: 18px; /* 增加字体大小 */
            color: #7f8c8d;
            font-weight: 400;
            line-height: 1.5;
        }
        
        .nav-menu {
            list-style: none;
            padding: 0 30px; /* 增加左右内边距 */
            flex-grow: 1;
        }
        
        .nav-menu li {
            margin-bottom: 10px; /* 增加间距 */
        }
        
        .nav-menu a {
            display: flex;
            align-items: center;
            padding: 18px 25px; /* 增加内边距 */
            color: #5d6d7e;
            text-decoration: none;
            border-radius: 10px; /* 增加圆角 */
            transition: all 0.3s ease;
            font-weight: 500;
            font-size: 16px; /* 增加字体大小 */
        }
        
        .nav-menu a i {
            margin-right: 15px; /* 增加图标间距 */
            font-size: 20px; /* 增加图标大小 */
            width: 28px; /* 增加图标容器宽度 */
            text-align: center;
        }
        
        .nav-menu a:hover {
            background-color: #eef5ff;
            color: #3498db;
        }
        
        .nav-menu a.active {
            background-color: #3498db;
            color: white;
            font-weight: 600;
            box-shadow: 0 4px 12px rgba(52, 152, 219, 0.3);
        }
        
        .sidebar-footer {
            padding: 30px 35px; /* 增加内边距 */
            margin-top: 40px;
            border-top: 1px solid #eaeaea;
        }
        
        .sidebar-footer p {
            color: #7f8c8d;
            font-size: 15px; /* 增加字体大小 */
            text-align: center;
            line-height: 1.6;
        }
        
        /* 右侧内容区 */
        .main-content {
            flex: 1;
            margin-left: 320px; /* 调整左边距以适应更宽的侧边栏 */
            background-color: white;
            min-height: 100vh;
        }
        
        /* 顶部横幅 */
        .banner {
            width: 100%;
            height: 400px;
            background-image: url('https://wallpaperm.cmcm.com/398f4912b45260cca24eb3ec9b37e711.jpg');
            background-size: cover;
            background-position: center;
            position: relative;
        }
        
        .banner-overlay {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            background: linear-gradient(to bottom, rgba(0,0,0,0.2), rgba(0,0,0,0.6));
            display: flex;
            align-items: center;
            justify-content: center;
        }
        
        .banner-content {
            text-align: center;
            color: white;
            max-width: 700px;
            padding: 0 20px;
        }
        
        .banner-content h1 {
            font-size: 42px;
            margin-bottom: 20px;
            text-shadow: 0 2px 5px rgba(0,0,0,0.5);
        }
        
        .banner-content p {
            font-size: 18px;
            opacity: 0.9;
        }
        
        /* 文章列表容器 */
        .posts-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 50px 40px;
        }
        
        .section-title {
            font-size: 28px;
            color: #2c3e50;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 3px solid #3498db;
        }
        
        /* 文章网格布局 */
        .posts-grid {
            display: grid;
            grid-template-columns: repeat(2, 1fr);
            gap: 30px;
        }
        
        /* 文章卡片 */
        .post-card {
            background-color: #ffffff;
            border-radius: 10px;
            padding: 30px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
            border: 1px solid #f0f0f0;
            transition: all 0.3s ease;
        }
        
        .post-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.08);
        }
        
        .post-category {
            display: inline-block;
            background-color: #e8f4fc;
            color: #3498db;
            padding: 6px 15px;
            border-radius: 20px;
            font-size: 14px;
            font-weight: 600;
            margin-bottom: 15px;
        }
        
        .post-title {
            font-size: 22px;
            color: #2c3e50;
            margin-bottom: 15px;
            line-height: 1.4;
        }
        
        .post-meta {
            color: #7f8c8d;
            font-size: 14px;
            margin-bottom: 20px;
            display: flex;
            align-items: center;
        }
        
        .post-meta i {
            margin-right: 8px;
        }
        
        .post-meta span {
            margin-right: 20px;
        }
        
        .post-excerpt {
            color: #555;
            line-height: 1.8;
            margin-bottom: 25px;
        }
        
        .read-more {
            display: inline-flex;
            align-items: center;
            color: #3498db;
            text-decoration: none;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        
        .read-more i {
            margin-left: 8px;
            transition: transform 0.3s ease;
        }
        
        .read-more:hover {
            color: #2c3e50;
        }
        
        .read-more:hover i {
            transform: translateX(5px);
        }
        
        /* 响应式设计 */
        @media (max-width: 1200px) {
            .posts-grid {
                grid-template-columns: 1fr;
            }
        }
        
        @media (max-width: 992px) {
            .sidebar {
                width: 100%;
                position: relative;
                height: auto;
                padding: 20px;
            }
            
            .main-content {
                margin-left: 0;
            }
            
            .banner {
                height: 300px;
            }
            
            .banner-content h1 {
                font-size: 32px;
            }
            
            .posts-container {
                padding: 30px 20px;
            }
        }
        
        @media (max-width: 768px) {
            .banner-content h1 {
                font-size: 28px;
            }
            
            .banner-content p {
                font-size: 16px;
            }
            
            .post-card {
                padding: 20px;
            }
            
            .post-title {
                font-size: 20px;
            }
            
            .section-title {
                font-size: 24px;
            }
        }
        
        /* 滚动条样式 */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: #f1f1f1;
        }
        
        ::-webkit-scrollbar-thumb {
            background: #3498db;
            border-radius: 4px;
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: #2980b9;
        }
        
        /* 页脚 */
        .footer {
            background-color: #2c3e50;
            color: white;
            padding: 40px 0;
            text-align: center;
        }
        
        .footer-content {
            max-width: 1200px;
            margin: 0 auto;
            padding: 0 20px;
        }
        
        .footer-links {
            display: flex;
            justify-content: center;
            gap: 30px;
            margin-bottom: 20px;
        }
        
        .footer-links a {
            color: #ddd;
            text-decoration: none;
        }
        
        .footer-links a:hover {
            color: #3498db;
        }
        
        .copyright {
            color: #aaa;
            font-size: 14px;
        }
    </style>
</head>
<body>
    <!-- 左侧导览栏 - 拉长版 -->
    <aside class="sidebar">
        <div class="blog-info">
            <h1 class="blog-title">风吹日晓</h1>
            <p class="blog-subtitle">探索技术与生活之美</p>
        </div>
        
        <ul class="nav-menu">
            <li><a href="#" class="active"><i class="fas fa-home"></i> 首页</a></li>
            <li><a href="#"><i class="fas fa-pen"></i> 文章</a></li>
            <li><a href="#"><i class="fas fa-folder"></i> 分类</a></li>
            <li><a href="#"><i class="fas fa-user"></i> 关于</a></li>
            <li><a href="#"><i class="fas fa-envelope"></i> 联系</a></li>
            <li><a href="#"><i class="fas fa-search"></i> 搜索</a></li>
        </ul>
        
        <div class="sidebar-footer">
            <p>© 2023 风吹日晓的个人博客</p>
            <p>记录思考，分享知识</p>
        </div>
    </aside>
    
    <!-- 右侧内容区 -->
    <main class="main-content">
        <!-- 顶部横幅 -->
        <div class="banner">
            <div class="banner-overlay">
                <div class="banner-content">
                    <h1>欢迎来到我的个人博客</h1>
                    <p>在这里，我将分享技术见解、生活感悟与学习心得，与你一同探索的世界</p>
                </div>
            </div>
        </div>
        
        <!-- 文章列表 -->
        <div class="posts-container">
            <h2 class="section-title">最新文章</h2>
            
            <div class="posts-grid">
                <!-- 左栏文章1 -->
                <article class="post-card">
                    <span class="post-category">算法与数据结构</span>
                    <h3 class="post-title">动态规划实战：解决经典背包问题</h3>
                    <div class="post-meta">
                        <span><i class="far fa-calendar"></i> 2023年10月10日</span>
                        <span><i class="far fa-eye"></i> 1.8k浏览</span>
                    </div>
                    <p class="post-excerpt">
                        动态规划是解决优化问题的强大技术。本文通过经典的0-1背包问题，详细讲解动态规划的核心思想、状态转移方程的建立，以及如何将算法应用到实际问题中。
                    </p>
                    <a href="#" class="read-more">阅读全文 <i class="fas fa-arrow-right"></i></a>
                </article>
                
                <!-- 右栏文章1 -->
                <article class="post-card">
                    <span class="post-category">生活随笔</span>
                    <h3 class="post-title">保持学习动力的五个有效方法</h3>
                    <div class="post-meta">
                        <span><i class="far fa-calendar"></i> 2023年10月5日</span>
                        <span><i class="far fa-eye"></i> 1.5k浏览</span>
                    </div>
                    <p class="post-excerpt">
                        在漫长而曲折的学习道路上，保持动力是一个永恒的话题。通过多年的学习经验，我总结了五个有效的方法，帮助我在技术快速迭代的时代保持持续学习和进步的热情。
                    </p>
                    <a href="#" class="read-more">阅读全文 <i class="fas fa-arrow-right"></i></a>
                </article>
                
                <!-- 左栏文章2 -->
                <article class="post-card">
                    <span class="post-category">前端开发</span>
                    <h3 class="post-title">探索CSS Grid布局的无限可能</h3>
                    <div class="post-meta">
                        <span><i class="far fa-calendar"></i> 2023年10月15日</span>
                        <span><i class="far fa-eye"></i> 2.1k浏览</span>
                    </div>
                    <p class="post-excerpt">
                        CSS Grid布局是现代网页设计的强大工具。通过灵活的网格系统，我们可以创建复杂且响应式的布局，而无需依赖外部框架。本文将深入探讨Grid的高级用法和实际案例。
                    </p>
                    <a href="#" class="read-more">阅读全文 <i class="fas fa-arrow-right"></i></a>
                </article>
                
                <!-- 右栏文章2 -->
                <article class="post-card">
                    <span class="post-category">JavaScript</span>
                    <h3 class="post-title">ES2023新特性详解与应用实践</h3>
                    <div class="post-meta">
                        <span><i class="far fa-calendar"></i> 2023年10月12日</span>
                        <span><i class="far fa-eye"></i> 2.5k浏览</span>
                    </div>
                    <p class="post-excerpt">
                        每年ECMAScript都会带来新的语言特性，ES2023也不例外。从数组查找方法到符号作为WeakMap键，这些新特性让JavaScript更加强大和易用。让我们一起来看看这些新特性如何提升开发效率。
                    </p>
                    <a href="#" class="read-more">阅读全文 <i class="fas fa-arrow-right"></i></a>
                </article>
            </div>
        </div>
        
        <!-- 页脚 -->
        <footer class="footer">
            <div class="footer-content">
                <div class="footer-links">
                    <a href="#">关于本站</a>
                    <a href="#">友情链接</a>
                    <a href="#">隐私政策</a>
                    <a href="#">版权声明</a>
                </div>
                <p class="copyright">© 2023 风吹日晓的个人博客 | 保留所有权利</p>
            </div>
        </footer>
    </main>

    <script>
        // 简单的交互效果
        document.addEventListener('DOMContentLoaded', function() {
            // 导航菜单交互
            const navLinks = document.querySelectorAll('.nav-menu a');
            
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    // 阻止默认跳转行为（因为是单页示例）
                    e.preventDefault();
                    
                    // 移除所有active类
                    navLinks.forEach(item => item.classList.remove('active'));
                    
                    // 为当前点击的链接添加active类
                    this.classList.add('active');
                    
                    // 更新横幅标题
                    const pageTitle = this.querySelector('i').nextSibling.textContent.trim();
                    const bannerTitle = document.querySelector('.banner-content h1');
                    
                    if (pageTitle === "首页") {
                        bannerTitle.textContent = "欢迎来到我的个人博客";
                    } else {
                        bannerTitle.textContent = `欢迎来到${pageTitle}页面`;
                    }
                });
            });
            
            // 文章卡片动画效果
            const postCards = document.querySelectorAll('.post-card');
            postCards.forEach((card, index) => {
                card.style.opacity = '0';
                card.style.transform = 'translateY(20px)';
                
                setTimeout(() => {
                    card.style.transition = 'opacity 0.5s ease, transform 0.5s ease';
                    card.style.opacity = '1';
                    card.style.transform = 'translateY(0)';
                }, 100 + index * 100);
            });
            
            // 页面加载动画
            document.body.style.opacity = '0';
            document.body.style.transition = 'opacity 0.5s ease';
            
            setTimeout(() => {
                document.body.style.opacity = '1';
            }, 100);
        });
    </script>
</body>
</html>
