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
            background-image: url('https://wallpaperm.cmcm.com/398f4912b45260cca24eb3ec9b37e711.jpg');
            background-size: cover;
            background-attachment: fixed;
            background-position: center;
            color: #333;
            min-height: 100vh;
            display: flex;
            line-height: 1.6;
        }
        
        /* 左侧导航栏 */
        .sidebar {
            width: 250px;
            background-color: rgba(255, 255, 255, 0.92);
            backdrop-filter: blur(10px);
            padding: 40px 25px;
            box-shadow: 5px 0 25px rgba(0, 0, 0, 0.08);
            display: flex;
            flex-direction: column;
            position: sticky;
            top: 0;
            height: 100vh;
            overflow-y: auto;
        }
        
        .blog-header {
            margin-bottom: 40px;
            text-align: center;
        }
        
        .blog-title {
            font-size: 28px;
            font-weight: 700;
            color: #2c3e50;
            margin-bottom: 10px;
            line-height: 1.3;
        }
        
        .blog-subtitle {
            font-size: 14px;
            color: #7f8c8d;
            font-weight: 500;
        }
        
        .nav-menu {
            list-style: none;
            flex-grow: 1;
        }
        
        .nav-menu li {
            margin-bottom: 12px;
        }
        
        .nav-menu a {
            display: flex;
            align-items: center;
            padding: 14px 18px;
            color: #34495e;
            text-decoration: none;
            border-radius: 10px;
            transition: all 0.3s ease;
            font-weight: 600;
        }
        
        .nav-menu a i {
            margin-right: 12px;
            font-size: 18px;
            width: 24px;
            text-align: center;
        }
        
        .nav-menu a:hover {
            background-color: #3498db;
            color: white;
            transform: translateX(5px);
        }
        
        .nav-menu a.active {
            background-color: #2c3e50;
            color: white;
        }
        
        .sidebar-footer {
            padding-top: 20px;
            border-top: 1px solid #eee;
            margin-top: 20px;
        }
        
        .social-links {
            display: flex;
            justify-content: center;
            gap: 15px;
        }
        
        .social-links a {
            display: flex;
            align-items: center;
            justify-content: center;
            width: 40px;
            height: 40px;
            background-color: #3498db;
            color: white;
            border-radius: 50%;
            text-decoration: none;
            transition: all 0.3s ease;
        }
        
        .social-links a:hover {
            background-color: #2c3e50;
            transform: translateY(-3px);
        }
        
        /* 主内容区 */
        .main-content {
            flex: 1;
            padding: 40px 60px;
            background-color: rgba(255, 255, 255, 0.88);
            backdrop-filter: blur(5px);
            overflow-y: auto;
            max-height: 100vh;
        }
        
        .welcome-section {
            margin-bottom: 50px;
        }
        
        .welcome-title {
            font-size: 36px;
            color: #2c3e50;
            margin-bottom: 20px;
        }
        
        .welcome-text {
            font-size: 18px;
            color: #555;
            max-width: 800px;
        }
        
        .posts-section {
            margin-top: 40px;
        }
        
        .section-title {
            font-size: 28px;
            color: #2c3e50;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 3px solid #3498db;
            display: inline-block;
        }
        
        .posts-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));
            gap: 30px;
            margin-top: 30px;
        }
        
        .post-card {
            background-color: white;
            border-radius: 15px;
            padding: 30px;
            box-shadow: 0 8px 25px rgba(0, 0, 0, 0.07);
            transition: all 0.3s ease;
            border: 1px solid rgba(0, 0, 0, 0.05);
        }
        
        .post-card:hover {
            transform: translateY(-10px);
            box-shadow: 0 15px 35px rgba(0, 0, 0, 0.1);
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
        @media (max-width: 1024px) {
            .sidebar {
                width: 220px;
                padding: 30px 20px;
            }
            
            .main-content {
                padding: 30px 40px;
            }
        }
        
        @media (max-width: 768px) {
            body {
                flex-direction: column;
            }
            
            .sidebar {
                width: 100%;
                height: auto;
                position: relative;
                padding: 20px;
                flex-direction: row;
                flex-wrap: wrap;
                justify-content: space-between;
            }
            
            .blog-header {
                width: 100%;
                margin-bottom: 20px;
            }
            
            .nav-menu {
                width: 100%;
                display: flex;
                flex-wrap: wrap;
                gap: 10px;
                justify-content: center;
            }
            
            .nav-menu li {
                margin-bottom: 0;
            }
            
            .nav-menu a {
                padding: 10px 15px;
            }
            
            .sidebar-footer {
                width: 100%;
                margin-top: 20px;
            }
            
            .main-content {
                padding: 30px 20px;
                max-height: none;
            }
            
            .posts-grid {
                grid-template-columns: 1fr;
            }
        }
        
        @media (max-width: 480px) {
            .welcome-title {
                font-size: 28px;
            }
            
            .welcome-text {
                font-size: 16px;
            }
            
            .section-title {
                font-size: 24px;
            }
            
            .post-card {
                padding: 20px;
            }
            
            .post-title {
                font-size: 20px;
            }
        }
        
        /* 滚动条样式 */
        ::-webkit-scrollbar {
            width: 8px;
        }
        
        ::-webkit-scrollbar-track {
            background: rgba(255, 255, 255, 0.1);
        }
        
        ::-webkit-scrollbar-thumb {
            background: #3498db;
            border-radius: 4px;
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: #2980b9;
        }
    </style>
</head>
<body>
    <!-- 左侧导航栏 -->
    <aside class="sidebar">
        <div class="blog-header">
            <h1 class="blog-title">风吹日晓</h1>
            <p class="blog-subtitle">个人博客 & 技术分享</p>
        </div>
        
        <ul class="nav-menu">
            <li><a href="#" class="active"><i class="fas fa-home"></i> 首页</a></li>
            <li><a href="#"><i class="fas fa-pen"></i> 文章</a></li>
            <li><a href="#"><i class="fas fa-folder"></i> 分类</a></li>
            <li><a href="#"><i class="fas fa-user"></i> 关于</a></li>
            <li><a href="#"><i class="fas fa-envelope"></i> 联系</a></li>
            <li><a href="#"><i class="fas fa-tags"></i> 标签</a></li>
            <li><a href="#"><i class="fas fa-archive"></i> 归档</a></li>
            <li><a href="#"><i class="fas fa-search"></i> 搜索</a></li>
        </ul>
        
        <div class="sidebar-footer">
            <div class="social-links">
                <a href="#" title="GitHub"><i class="fab fa-github"></i></a>
                <a href="#" title="微博"><i class="fab fa-weibo"></i></a>
                <a href="#" title="知乎"><i class="fab fa-zhihu"></i></a>
                <a href="#" title="邮箱"><i class="fas fa-envelope"></i></a>
            </div>
        </div>
    </aside>
    
    <!-- 主内容区 -->
    <main class="main-content">
        <section class="welcome-section">
            <h1 class="welcome-title">欢迎来到我的个人空间</h1>
            <p class="welcome-text">
                我是风吹日晓，一名热爱技术与分享的开发者。这里记录了我的学习历程、技术心得和生活感悟。我相信代码可以改变世界，而分享则能让知识传递更远。在这个快速变化的数字时代，我希望通过这个博客与志同道合的朋友们交流、学习、共同成长。
            </p>
        </section>
        
        <section class="posts-section">
            <h2 class="section-title">最新文章</h2>
            
            <div class="posts-grid">
                <!-- 文章1 -->
                <article class="post-card">
                    <span class="post-category">前端开发</span>
                    <h3 class="post-title">探索CSS Grid布局的无限可能</h3>
                    <div class="post-meta">
                        <span><i class="far fa-calendar"></i> 2023年10月20日</span>
                        <span><i class="far fa-eye"></i> 1.2k浏览</span>
                    </div>
                    <p class="post-excerpt">
                        CSS Grid布局是现代网页设计的强大工具。通过灵活的网格系统，我们可以创建复杂且响应式的布局，而无需依赖外部框架。本文将深入探讨Grid的高级用法和实际案例。
                    </p>
                    <a href="#" class="read-more">阅读全文 <i class="fas fa-arrow-right"></i></a>
                </article>
                
                <!-- 文章2 -->
                <article class="post-card">
                    <span class="post-category">JavaScript</span>
                    <h3 class="post-title">ES2023新特性详解与应用实践</h3>
                    <div class="post-meta">
                        <span><i class="far fa-calendar"></i> 2023年10月15日</span>
                        <span><i class="far fa-eye"></i> 2.1k浏览</span>
                    </div>
                    <p class="post-excerpt">
                        每年ECMAScript都会带来新的语言特性，ES2023也不例外。从数组查找方法到符号作为WeakMap键，这些新特性让JavaScript更加强大和易用。让我们一起来看看这些新特性如何提升开发效率。
                    </p>
                    <a href="#" class="read-more">阅读全文 <i class="fas fa-arrow-right"></i></a>
                </article>
                
                <!-- 文章3 -->
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
                
                <!-- 文章4 -->
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
                
                <!-- 文章5 -->
                <article class="post-card">
                    <span class="post-category">工具推荐</span>
                    <h3 class="post-title">2023年开发者必备的十个VS Code插件</h3>
                    <div class="post-meta">
                        <span><i class="far fa-calendar"></i> 2023年9月28日</span>
                        <span><i class="far fa-eye"></i> 3.2k浏览</span>
                    </div>
                    <p class="post-excerpt">
                        Visual Studio Code是当今最受欢迎的代码编辑器之一，其强大的插件生态系统是它成功的关键。本文将介绍十个能够极大提升开发效率的VS Code插件，涵盖代码质量、Git集成、主题美化等方面。
                    </p>
                    <a href="#" class="read-more">阅读全文 <i class="fas fa-arrow-right"></i></a>
                </article>
                
                <!-- 文章6 -->
                <article class="post-card">
                    <span class="post-category">性能优化</span>
                    <h3 class="post-title">现代前端性能优化策略全解析</h3>
                    <div class="post-meta">
                        <span><i class="far fa-calendar"></i> 2023年9月20日</span>
                        <span><i class="far fa-eye"></i> 2.5k浏览</span>
                    </div>
                    <p class="post-excerpt">
                        在用户体验至上的今天，前端性能优化变得尤为重要。本文将从加载优化、渲染优化、资源优化等多个维度，系统性地介绍现代前端性能优化的最新策略和最佳实践。
                    </p>
                    <a href="#" class="read-more">阅读全文 <i class="fas fa-arrow-right"></i></a>
                </article>
            </div>
        </section>
    </main>

    <script>
        // 简单的交互效果
        document.addEventListener('DOMContentLoaded', function() {
            // 导航菜单交互
            const navLinks = document.querySelectorAll('.nav-menu a');
            
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
                    // 移除所有active类
                    navLinks.forEach(item => item.classList.remove('active'));
                    // 为当前点击的链接添加active类
                    this.classList.add('active');
                });
            });
            
            // 文章卡片动画延迟
            const postCards = document.querySelectorAll('.post-card');
            postCards.forEach((card, index) => {
                card.style.animationDelay = `${index * 0.1}s`;
            });
            
            // 页面加载时的简单动画
            setTimeout(() => {
                document.body.style.opacity = '1';
            }, 100);
            
            // 初始透明度设置为0，然后淡入
            document.body.style.opacity = '0';
            document.body.style.transition = 'opacity 0.5s ease';
        });
    </script>
</body>
</html>
