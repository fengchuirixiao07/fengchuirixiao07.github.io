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
        
        /* 文章阅读容器 - 初始隐藏 */
        .article-container {
            max-width: 1100px;
            margin: 0 auto;
            padding: 50px 40px;
            display: none;
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
            cursor: pointer;
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
        
        /* 返回文章列表按钮 */
        .back-to-posts-btn {
            display: inline-flex;
            align-items: center;
            background-color: #3498db;
            color: white;
            border: none;
            border-radius: 8px;
            padding: 12px 20px;
            font-size: 16px;
            font-weight: 600;
            cursor: pointer;
            margin-bottom: 30px;
            transition: all 0.3s ease;
        }
        
        .back-to-posts-btn:hover {
            background-color: #2980b9;
            transform: translateX(-5px);
        }
        
        .back-to-posts-btn i {
            margin-right: 10px;
        }
        
        /* 文章内容样式 */
        .article-content {
            background-color: #ffffff;
            border-radius: 10px;
            padding: 40px;
            box-shadow: 0 5px 20px rgba(0, 0, 0, 0.05);
            border: 1px solid #f0f0f0;
        }
        
        .article-title {
            font-size: 32px;
            color: #2c3e50;
            margin-bottom: 20px;
            padding-bottom: 15px;
            border-bottom: 2px solid #3498db;
        }
        
        .article-meta {
            color: #7f8c8d;
            font-size: 15px;
            margin-bottom: 30px;
            display: flex;
            align-items: center;
        }
        
        .article-meta i {
            margin-right: 8px;
        }
        
        .article-meta span {
            margin-right: 20px;
        }
        
        .article-body {
            color: #333;
            font-size: 16px;
            line-height: 1.8;
        }
        
        .article-body h2 {
            color: #2c3e50;
            margin: 30px 0 15px;
            font-size: 24px;
            padding-bottom: 10px;
            border-bottom: 1px solid #eee;
        }
        
        .article-body h3 {
            color: #2c3e50;
            margin: 25px 0 10px;
            font-size: 20px;
        }
        
        .article-body p {
            margin-bottom: 15px;
        }
        
        .article-body ul, .article-body ol {
            margin-left: 20px;
            margin-bottom: 15px;
        }
        
        .article-body li {
            margin-bottom: 8px;
        }
        
        .article-body code {
            background-color: #f5f5f5;
            padding: 2px 6px;
            border-radius: 4px;
            font-family: 'Courier New', monospace;
            font-size: 14px;
        }
        
        .article-body pre {
            background-color: #2c3e50;
            color: #ecf0f1;
            padding: 15px;
            border-radius: 8px;
            overflow-x: auto;
            margin: 15px 0;
            font-family: 'Courier New', monospace;
            font-size: 14px;
        }
        
        .article-body blockquote {
            border-left: 4px solid #3498db;
            padding-left: 15px;
            margin: 15px 0;
            color: #666;
            font-style: italic;
        }
        
        /* 响应式设计 */
        @media (max-width: 1400px) {
            .sidebar {
                width: 380px;
            }
            
            .main-content {
                margin-left: 380px;
            }
            
            .posts-container, .article-container {
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
            
            .posts-container, .article-container {
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
            
            .posts-container, .article-container {
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
            
            .article-content {
                padding: 25px;
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
            
            .article-title {
                font-size: 26px;
            }
            
            .article-body h2 {
                font-size: 22px;
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
            
            <!-- 第一篇文章卡片 -->
            <div class="post-link-card" id="article1Card">
                <div class="post-icon">
                    <i class="fas fa-lock"></i>
                </div>
                <div class="post-link-content">
                    <h3 class="post-link-title">start basic crypto</h3>
                    <p class="post-link-description">这篇文档系统性地介绍了基础密码学知识，涵盖RSA加密原理、共享素数攻击、中国剩余定理、小明文攻击、费马小定理及其应用、dp泄露攻击、线性同余生成器(LCG)以及椭圆曲线数字签名算法(ECDSA)等内容。</p>
                    <div class="post-link-meta">
                        <span><i class="far fa-user"></i> 风吹日晓</span>
                        <span><i class="far fa-calendar"></i> 2026年2月15日</span>
                    </div>
                </div>
            </div>
            
            <!-- 第二篇文章卡片 -->
            <div class="post-link-card" id="article2Card">
                <div class="post-icon">
                    <i class="fas fa-calendar-week"></i>
                </div>
                <div class="post-link-content">
                    <h3 class="post-link-title">第三周周报</h3>
                    <p class="post-link-description">这是第三周的学习周报，记录了本周的学习进展、技术实践、遇到的问题及解决方案，以及对下一周学习计划的安排。</p>
                    <div class="post-link-meta">
                        <span><i class="far fa-user"></i> 风吹日晓</span>
                        <span><i class="far fa-calendar"></i> 2026年2月10日</span>
                    </div>
                </div>
            </div>
        </div>
        
        <!-- 第一篇文章阅读容器 -->
        <div class="article-container" id="article1Container">
            <button class="back-to-posts-btn" onclick="showPosts()">
                <i class="fas fa-arrow-left"></i> 返回文章列表
            </button>
            
            <div class="article-content">
                <h1 class="article-title">start basic crypto</h1>
                <div class="article-meta">
                    <span><i class="far fa-calendar"></i> 2026年2月15日</span>
                    <span><i class="far fa-user"></i> 作者：风吹日晓</span>
                </div>
                
                <div class="article-body">
                    <h2>基础密码学知识概述</h2>
                    <p>这篇文档系统性地介绍了基础密码学知识，涵盖RSA加密原理、共享素数攻击、中国剩余定理、小明文攻击、费马小定理及其应用、dp泄露攻击、线性同余生成器(LCG)以及椭圆曲线数字签名算法(ECDSA)等内容。</p>
                    
                    <h3>RSA加密原理</h3>
                    <p>RSA是一种非对称加密算法，其安全性基于大整数分解的困难性。算法主要包括密钥生成、加密和解密三个步骤。</p>
                    
                    <h3>密钥生成过程：</h3>
                    <ol>
                        <li>选择两个大素数p和q</li>
                        <li>计算n = p × q</li>
                        <li>计算φ(n) = (p-1) × (q-1)</li>
                        <li>选择整数e，满足1 < e < φ(n)且gcd(e, φ(n)) = 1</li>
                        <li>计算d，满足d × e ≡ 1 mod φ(n)</li>
                    </ol>
                    
                    <p>公钥为(e, n)，私钥为(d, n)。加密过程为：c = m^e mod n；解密过程为：m = c^d mod n。</p>
                    
                    <h3>共享素数攻击</h3>
                    <p>当多个RSA密钥共享同一个素数时，可以通过计算gcd(n1, n2)来分解模数，从而破解密钥。</p>
                    
                    <pre><code>def shared_prime_attack(n1, n2):
    p = gcd(n1, n2)
    if p != 1:
        q1 = n1 // p
        q2 = n2 // p
        return p, q1, q2
    return None</code></pre>
                    
                    <h3>中国剩余定理(CRT)</h3>
                    <p>中国剩余定理用于求解同余方程组，在RSA中有重要应用，可以加速解密过程。</p>
                    
                    <blockquote>如果一组同余方程模数两两互质，则方程组有唯一解模所有模数的乘积。</blockquote>
                    
                    <h3>小明文攻击</h3>
                    <p>当明文m很小且加密指数e也很小时，密文c = m^e mod n可能小于n，此时可以通过直接开e次方得到明文。</p>
                    
                    <h3>费马小定理及其应用</h3>
                    <p>费马小定理：如果p是质数，a是整数且p不整除a，则a^(p-1) ≡ 1 mod p。</p>
                    
                    <h3>dp泄露攻击</h3>
                    <p>如果泄露了d mod (p-1)，即dp，可以高效地分解n，从而破解RSA。</p>
                    
                    <h3>线性同余生成器(LCG)</h3>
                    <p>LCG是生成伪随机数的一种算法，公式为：X_{n+1} = (a × X_n + c) mod m。</p>
                    
                    <h3>椭圆曲线数字签名算法(ECDSA)</h3>
                    <p>ECDSA是基于椭圆曲线密码学的数字签名算法，相比RSA具有更高的安全性和更短的密钥长度。</p>
                    
                    <h2>总结</h2>
                    <p>密码学是信息安全的基础，理解这些基础概念和攻击方法对于深入学习和应用密码学至关重要。在实际应用中，需要选择合适的参数并遵循最佳实践，以确保系统的安全性。</p>
                </div>
            </div>
        </div>
        
        <!-- 第二篇文章阅读容器 -->
        <div class="article-container" id="article2Container">
            <button class="back-to-posts-btn" onclick="showPosts()">
                <i class="fas fa-arrow-left"></i> 返回文章列表
            </button>
            
            <div class="article-content">
                <h1 class="article-title">第三周周报</h1>
                <div class="article-meta">
                    <span><i class="far fa-calendar"></i> 2026年2月10日</span>
                    <span><i class="far fa-user"></i> 作者：风吹日晓</span>
                </div>
                
                <div class="article-body">
                    <h2>本周学习进展</h2>
                    <p>这是第三周的学习周报，记录了本周的学习进展、技术实践、遇到的问题及解决方案，以及对下一周学习计划的安排。</p>
                    
                    <h3>密码学学习</h3>
                    <p>本周主要学习了基础密码学知识，包括：</p>
                    <ul>
                        <li>RSA加密算法原理及实现</li>
                        <li>常见RSA攻击方法（共享素数攻击、小明文攻击等）</li>
                        <li>中国剩余定理在密码学中的应用</li>
                        <li>椭圆曲线密码学基础</li>
                    </ul>
                    
                    <h3>技术实践</h3>
                    <p>通过实际编码实践了以下内容：</p>
                    
                    <pre><code># RSA密钥生成示例
import random
import math

def is_prime(n, k=5):
    if n < 2:
        return False
    for _ in range(k):
        a = random.randint(2, n-1)
        if pow(a, n-1, n) != 1:
            return False
    return True

def generate_rsa_key(bits=1024):
    # 生成大素数
    p = q = 0
    while p == q:
        p = random.getrandbits(bits)
        q = random.getrandbits(bits)
        while not is_prime(p):
            p += 1
        while not is_prime(q):
            q += 1
    
    n = p * q
    phi = (p-1) * (q-1)
    
    # 选择e
    e = 65537
    while math.gcd(e, phi) != 1:
        e += 2
    
    # 计算d
    d = pow(e, -1, phi)
    
    return (e, n), (d, n)</code></pre>
                    
                    <h3>遇到的问题及解决方案</h3>
                    <h4>问题1：RSA大整数运算效率低</h4>
                    <p>在Python中直接进行大整数幂运算时，遇到了性能问题。</p>
                    <p><strong>解决方案：</strong> 使用Python内置的pow()函数的三参数形式：pow(a, b, mod)，这样可以高效地进行模幂运算。</p>
                    
                    <h4>问题2：素数检测算法选择</h4>
                    <p>对于大素数的检测，简单的试除法效率太低。</p>
                    <p><strong>解决方案：</strong> 实现了Miller-Rabin素性测试算法，大大提高了素数检测的效率。</p>
                    
                    <h3>收获与心得</h3>
                    <p>通过本周的学习，我对密码学有了更深入的理解：</p>
                    <ol>
                        <li>理解了非对称加密的基本原理和RSA算法的数学基础</li>
                        <li>掌握了常见的RSA攻击方法和防御策略</li>
                        <li>通过实践加深了对密码学算法实现的理解</li>
                        <li>认识到在实际应用中参数选择的重要性</li>
                    </ol>
                    
                    <blockquote>密码学的核心在于数学，理解其背后的数学原理比单纯使用API更重要。</blockquote>
                    
                    <h3>下周学习计划</h3>
                    <p>基于本周的学习进展，下周计划：</p>
                    <ul>
                        <li>深入学习椭圆曲线密码学(ECC)</li>
                        <li>研究数字签名算法的实现和应用</li>
                        <li>实践TLS/SSL协议中的密码学应用</li>
                        <li>探索区块链中的密码学技术</li>
                    </ul>
                    
                    <h2>总结</h2>
                    <p>本周的学习充实而有收获，密码学是一个深奥但有趣的领域。通过理论与实践相结合的方式，我对这个领域有了更深入的理解。期待下周继续探索密码学的奥秘。</p>
                </div>
            </div>
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
        // 显示文章列表，隐藏所有文章容器
        function showPosts() {
            document.getElementById('postsContainer').style.display = 'block';
            document.getElementById('article1Container').style.display = 'none';
            document.getElementById('article2Container').style.display = 'none';
            
            // 滚动到顶部
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        }
        
        // 显示指定的文章
        function showArticle(articleId) {
            document.getElementById('postsContainer').style.display = 'none';
            document.getElementById('article1Container').style.display = 'none';
            document.getElementById('article2Container').style.display = 'none';
            
            document.getElementById(articleId + 'Container').style.display = 'block';
            
            // 滚动到顶部
            window.scrollTo({
                top: 0,
                behavior: 'smooth'
            });
        }
        
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
                    
                    // 如果点击的是首页，显示文章列表
                    const pageTitle = this.querySelector('i').nextSibling.textContent.trim();
                    if (pageTitle === "首页") {
                        showPosts();
                    }
                });
            });
            
            // 文章卡片点击事件
            document.getElementById('article1Card').addEventListener('click', function() {
                showArticle('article1');
            });
            
            document.getElementById('article2Card').addEventListener('click', function() {
                showArticle('article2');
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
