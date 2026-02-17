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
        
        /* 左侧导览栏 */
        .sidebar {
            width: 400px;
            background-color: #f8f9fa;
            border-right: 1px solid #eaeaea;
            padding: 60px 0;
            position: fixed;
            top: 0;
            left: 0;
            bottom: 0;
            overflow-y: auto;
            display: flex;
            flex-direction: column;
        }
        
        .blog-info {
            padding: 0 45px;
            margin-bottom: 80px;
            text-align: center;
        }
        
        .blog-title {
            font-size: 38px;
            font-weight: 700;
            color: #2c3e50;
            margin-bottom: 15px;
            letter-spacing: 1px;
        }
        
        .blog-subtitle {
            font-size: 22px;
            color: #7f8c8d;
            font-weight: 400;
            line-height: 1.5;
        }
        
        .nav-menu {
            list-style: none;
            padding: 0 40px;
            flex-grow: 1;
        }
        
        .nav-menu li {
            margin-bottom: 15px;
        }
        
        .nav-menu a {
            display: flex;
            align-items: center;
            padding: 22px 30px;
            color: #5d6d7e;
            text-decoration: none;
            border-radius: 12px;
            transition: all 0.3s ease;
            font-weight: 500;
            font-size: 20px;
        }
        
        .nav-menu a i {
            margin-right: 20px;
            font-size: 24px;
            width: 32px;
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
            padding: 40px 45px;
            margin-top: 60px;
            border-top: 1px solid #eaeaea;
            text-align: center;
        }
        
        .sidebar-footer p {
            color: #7f8c8d;
            font-size: 18px;
            line-height: 1.6;
        }
        
        /* 右侧内容区 */
        .main-content {
            flex: 1;
            margin-left: 400px;
            background-color: white;
            min-height: 100vh;
            overflow-x: hidden;
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
            max-width: 1100px;
            margin: 0 auto;
            padding: 50px 40px;
            display: block;
        }
        
        .section-title {
            font-size: 28px;
            color: #2c3e50;
            margin-bottom: 30px;
            padding-bottom: 15px;
            border-bottom: 3px solid #3498db;
        }
        
        /* 文章链接卡片 */
        .post-link-card {
            background-color: #ffffff;
            border-radius: 10px;
            padding: 30px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
            border: 1px solid #f0f0f0;
            transition: all 0.3s ease;
            margin-bottom: 30px;
            display: flex;
            align-items: center;
            text-decoration: none;
            color: inherit;
        }
        
        .post-link-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
            border-color: #3498db;
            text-decoration: none;
        }
        
        .post-icon {
            width: 60px;
            height: 60px;
            background-color: #e8f4fc;
            border-radius: 12px;
            display: flex;
            align-items: center;
            justify-content: center;
            margin-right: 25px;
            color: #3498db;
            font-size: 24px;
            flex-shrink: 0;
        }
        
        .post-link-content {
            flex: 1;
        }
        
        .post-link-title {
            font-size: 22px;
            color: #2c3e50;
            margin-bottom: 10px;
            line-height: 1.4;
        }
        
        .post-link-description {
            color: #7f8c8d;
            font-size: 16px;
            margin-bottom: 15px;
        }
        
        .post-link-meta {
            color: #7f8c8d;
            font-size: 14px;
            display: flex;
            align-items: center;
        }
        
        .post-link-meta span {
            margin-right: 20px;
            display: flex;
            align-items: center;
        }
        
        .post-link-meta i {
            margin-right: 8px;
        }
        
        /* 响应式设计 */
        @media (max-width: 1400px) {
            .sidebar {
                width: 380px;
            }
            
            .main-content {
                margin-left: 380px;
            }
            
            .posts-container {
                max-width: 1000px;
            }
        }
        
        @media (max-width: 1200px) {
            .sidebar {
                width: 350px;
            }
            
            .main-content {
                margin-left: 350px;
            }
            
            .posts-container {
                max-width: 900px;
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
                max-width: 100%;
            }
            
            .post-link-card {
                flex-direction: column;
                text-align: center;
                padding: 25px;
            }
            
            .post-icon {
                margin-right: 0;
                margin-bottom: 20px;
            }
        }
        
        @media (max-width: 768px) {
            .banner-content h1 {
                font-size: 28px;
            }
            
            .banner-content p {
                font-size: 16px;
            }
            
            .post-link-title {
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
            max-width: 1100px;
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
    <!-- 左侧导览栏 -->
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
            <p>© 2026 风吹日晓的个人博客</p>
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
        <div class="posts-container" id="postsContainer">
            <h2 class="section-title">文章列表</h2>
            
            <!-- 第一篇文章卡片 - 链接到 basic crypto.html -->
            <a href="basic%20crypto.html" target="_blank" class="post-link-card">
                <div class="post-icon">
                    <i class="fas fa-lock"></i>
                </div>
                <div class="post-link-content">
                    <h3 class="post-link-title">start basic crypto</h3>
                    <p class="post-link-description">这篇文档系统性地介绍了基础密码学知识，涵盖RSA加密原理、共享素数攻击、中国剩余定理、小明文攻击、费马小定理及其应用、dp泄露攻击、线性同余生成器(LCG)以及椭圆曲线数字签名算法(ECDSA)等内容。</p>
                    <div class="post-link-meta">
                        <span><i class="far fa-user"></i> 风吹日晓</span>
                        <span><i class="far fa-calendar"></i> 2026年2月15日</span>
                        <span><i class="fas fa-external-link-alt"></i> 点击阅读全文</span>
                    </div>
                </div>
            </a>
            
            <!-- 第二篇文章卡片 - 链接到 three week.html -->
            <a href="three%20week.html" target="_blank" class="post-link-card">
                <div class="post-icon">
                    <i class="fas fa-calendar-week"></i>
                </div>
                <div class="post-link-content">
                    <h3 class="post-link-title">第三周周报</h3>
                    <p class="post-link-description">这是第三周的学习周报，记录了本周的学习进展、技术实践、遇到的问题及解决方案，以及对下一周学习计划的安排。</p>
                    <div class="post-link-meta">
                        <span><i class="far fa-user"></i> 风吹日晓</span>
                        <span><i class="far fa-calendar"></i> 2026年2月10日</span>
                        <span><i class="fas fa-external-link-alt"></i> 点击阅读全文</span>
                    </div>
                </div>
            </a>
            
            <!-- 示例文章卡片（保留用于未来文章） -->
            <a href="#" class="post-link-card">
                <div class="post-icon">
                    <i class="fas fa-code"></i>
                </div>
                <div class="post-link-content">
                    <h3 class="post-link-title">这里是文章标题</h3>
                    <p class="post-link-description">这里是文章的描述内容，简要介绍文章的主要内容和亮点，吸引读者点击阅读全文。这里可以放置一段较长的描述文字，展示文章的概要信息。</p>
                    <div class="post-link-meta">
                        <span><i class="far fa-user"></i> 作者名</span>
                        <span><i class="far fa-calendar"></i> 发布日期</span>
                    </div>
                </div>
            </a>
        </div>
        
        <!-- 页脚 -->
        <footer class="footer">
            <div class="footer-content">
                <div class="footer-links">
                    <a href="https://github.com/fengchuirixiao07" target="_blank">GitHub</a>
                    <a href="https://fengchuirixiao07.github.io/" target="_blank">博客主页</a>
                    <a href="#">友情链接</a>
                    <a href="#">版权声明</a>
                </div>
                <p class="copyright">© 2026 风吹日晓的个人博客 | 保留所有权利</p>
            </div>
        </footer>
    </main>

    <script>
        // 页面加载时的初始化
        document.addEventListener('DOMContentLoaded', function() {
            // 导航菜单交互
            const navLinks = document.querySelectorAll('.nav-menu a');
            
            navLinks.forEach(link => {
                link.addEventListener('click', function(e) {
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
            const postCards = document.querySelectorAll('.post-link-card');
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
