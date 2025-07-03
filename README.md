<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>吾书 - 网络书店系统</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Microsoft YaHei', sans-serif;
        }
        
        body {
            background-color: #f0ffff;
            color: #333;
            line-height: 1.6;
        }
        
        header {
            background-color: #ffaa33;
            color: white;
            padding: 1rem 0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1);
        }
        
        .container {
            width: 90%;
            max-width: 1200px;
            margin: 0 auto;
        }
        
        .header-content {
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        
        .logo {
            font-size: 1.8rem;
            font-weight: bold;
        }
        
        nav ul {
            display: flex;
            list-style: none;
        }
        
        nav ul li {
            margin-left: 1.5rem;
        }
        
        nav ul li a {
            color: white;
            text-decoration: none;
            font-weight: 500;
            transition: color 0.3s;
        }
        
        nav ul li a:hover {
            color: #de3163;
        }
        
        .auth-buttons a {
            margin-left: 1rem;
            padding: 0.5rem 1rem;
            border-radius: 4px;
            text-decoration: none;
            font-weight: 500;
        }
        
        .login-btn {
            color: white;
            border: 1px solid white;
        }
        
        .register-btn {
            background-color: #93c572;
            color: white;
        }
        
        main {
            padding: 2rem 0;
        }
        
        .page-title {
            margin-bottom: 2rem;
            color: #ffc000;
            border-bottom: 2px solid #f39c12;
            padding-bottom: 0.5rem;
            display: inline-block;
        }
        
        .book-list {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
            gap: 2rem;
        }
        
        .book-card {
            background-color: white;
            border-radius: 8px;
            overflow: hidden;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            transition: transform 0.3s;
        }
        
        .book-card:hover {
            transform: translateY(-5px);
        }
        
        .book-image {
            height: 200px;
            background-color: #eee;
            display: flex;
            align-items: center;
            justify-content: center;
            color: #777;
        }
        
        .book-info {
            padding: 1.5rem;
        }
        
        .book-title {
            font-size: 1.2rem;
            margin-bottom: 0.5rem;
            color: #ffd700;
        }
        
        .book-author {
            color: #7f8c8d;
            margin-bottom: 0.5rem;
        }
        
        .book-price {
            font-weight: bold;
            color: #e74c3c;
            margin-bottom: 1rem;
        }
        
        .book-actions {
            display: flex;
            justify-content: space-between;
        }
        
        .btn {
            padding: 0.5rem 1rem;
            border: none;
            border-radius: 4px;
            cursor: pointer;
            font-weight: 500;
            transition: background-color 0.3s;
        }
        
        .btn-primary {
            background-color: #3498db;
            color: white;
        }
        
        .btn-primary:hover {
            background-color: #2980b9;
        }
        
        .btn-danger {
            background-color: #e74c3c;
            color: white;
        }
        
        .btn-danger:hover {
            background-color: #c0392b;
        }
        
        .btn-success {
            background-color: #2ecc71;
            color: white;
        }
        
        .btn-success:hover {
            background-color: #27ae60;
        }
        
        .btn-warning {
            background-color: #f39c12;
            color: white;
        }
        
        .btn-warning:hover {
            background-color: #d35400;
        }
        
        .admin-actions {
            margin-bottom: 2rem;
        }
        
        form {
            background-color: white;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
            margin-bottom: 2rem;
        }
        
        .form-group {
            margin-bottom: 1.5rem;
        }
        
        label {
            display: block;
            margin-bottom: 0.5rem;
            font-weight: 500;
        }
        
        input, select, textarea {
            width: 100%;
            padding: 0.75rem;
            border: 1px solid #ddd;
            border-radius: 4px;
            font-size: 1rem;
        }
        
        textarea {
            min-height: 100px;
            resize: vertical;
        }
        
        .order-list {
            background-color: white;
            padding: 2rem;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.1);
        }
        
        table {
            width: 100%;
            border-collapse: collapse;
        }
        
        th, td {
            padding: 1rem;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }
        
        th {
            background-color: #f8f9fa;
            font-weight: 500;
        }
        
        footer {
            background-color: #ffc000;
            color: white;
            text-align: center;
            padding: 1.5rem 0;
            margin-top: 2rem;
        }
        
        .user-info {
            display: flex;
            align-items: center;
        }
        
        .user-info span {
            margin-right: 1rem;
            color: white;
        }
        
        .hidden {
            display: none;
        }
        
        .active {
            display: block;
        }
        
        .tab-buttons {
            display: flex;
            margin-bottom: 1rem;
            border-bottom: 1px solid #ddd;
        }
        
        .tab-btn {
            padding: 0.75rem 1.5rem;
            background-color: #f8f9fa;
            border: none;
            cursor: pointer;
            font-weight: 500;
            margin-right: 0.5rem;
            border-radius: 4px 4px 0 0;
        }
        
        .tab-btn.active {
            background-color: #3498db;
            color: white;
        }
    </style>
</head>
<body>
    <header>
        <div class="container header-content">
            <div class="logo">吾书</div>
            <nav>
                <ul>
                    <li><a href="#" onclick="showPage('home')">首页</a></li>
                    <li><a href="#" onclick="showPage('books')">图书浏览</a></li>
                    <li id="member-orders-link" class="hidden"><a href="#" onclick="showPage('orders')">我的订单</a></li>
                    <li id="admin-manage-link" class="hidden"><a href="#" onclick="showPage('manage')">图书管理</a></li>
                    <li><a href="#" onclick="showPage('about')">关于我们</a></li>
                </ul>
            </nav>
            <div class="auth-buttons" id="auth-buttons">
                <a href="#" class="login-btn" onclick="showPage('login')">登录</a>
                <a href="#" class="register-btn" onclick="showPage('register')">注册</a>
            </div>
            <div class="user-info hidden" id="user-info">
                <span id="username-display"></span>
                <a href="#" class="btn btn-warning" onclick="logout()">退出</a>
            </div>
        </div>
    </header>

    <main class="container">
        <!-- 首页 -->
        <section id="home" class="page active">
            <h1 class="page-title">欢迎来到吾书</h1>
            <p>我们提供各类图书，满足您的阅读需求。注册成为会员即可购买图书。</p>
            
            <h2 style="margin: 2rem 0 1rem;">热门图书</h2>
            <div class="book-list">
                <div class="book-card">
                    <img src="E:\桌面\新建文件夹\新建文件夹\OIP-C.jpg" width="280">
                    <div class="book-info">
                        <h3 class="book-title">JavaScript高级程序设计</h3>
                        <p class="book-author">作者: Nicholas C. Zakas</p>
                        <p class="book-price">¥89.00</p>
                        <div class="book-actions">
                            <button class="btn btn-primary" onclick="showPage('book-detail')">查看详情</button>
                            <button class="btn btn-success member-only hidden" onclick="addToCart(1)">加入购物车</button>
                        </div>
                    </div>
                </div>
                
                <div class="book-card">
                    <div class="book-image">图书封面</div>
                    <div class="book-info">
                        <h3 class="book-title">Python编程：从入门到实践</h3>
                        <p class="book-author">作者: Eric Matthes</p>
                        <p class="book-price">¥75.00</p>
                        <div class="book-actions">
                            <button class="btn btn-primary" onclick="showPage('book-detail')">查看详情</button>
                            <button class="btn btn-success member-only hidden" onclick="addToCart(2)">加入购物车</button>
                        </div>
                    </div>
                </div>
                
                <div class="book-card">
                    <div class="book-image">图书封面</div>
                    <div class="book-info">
                        <h3 class="book-title">活着</h3>
                        <p class="book-author">作者: 余华</p>
                        <p class="book-price">¥39.00</p>
                        <div class="book-actions">
                            <button class="btn btn-primary" onclick="showPage('book-detail')">查看详情</button>
                            <button class="btn btn-success member-only hidden" onclick="addToCart(3)">加入购物车</button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 图书浏览 -->
        <section id="books" class="page hidden">
            <h1 class="page-title">图书浏览</h1>
            
            <div class="book-list">
                <div class="book-card">
                    <div class="book-image">图书封面</div>
                    <div class="book-info">
                        <h3 class="book-title">JavaScript高级程序设计</h3>
                        <p class="book-author">作者: Nicholas C. Zakas</p>
                        <p class="book-price">¥89.00</p>
                        <div class="book-actions">
                            <button class="btn btn-primary" onclick="showPage('book-detail')">查看详情</button>
                            <button class="btn btn-success member-only hidden" onclick="addToCart(1)">加入购物车</button>
                        </div>
                    </div>
                </div>
                
                <div class="book-card">
                    <div class="book-image">图书封面</div>
                    <div class="book-info">
                        <h3 class="book-title">Python编程：从入门到实践</h3>
                        <p class="book-author">作者: Eric Matthes</p>
                        <p class="book-price">¥75.00</p>
                        <div class="book-actions">
                            <button class="btn btn-primary" onclick="showPage('book-detail')">查看详情</button>
                            <button class="btn btn-success member-only hidden" onclick="addToCart(2)">加入购物车</button>
                        </div>
                    </div>
                </div>
                
                <div class="book-card">
                    <div class="book-image">图书封面</div>
                    <div class="book-info">
                        <h3 class="book-title">活着</h3>
                        <p class="book-author">作者: 余华</p>
                        <p class="book-price">¥39.00</p>
                        <div class="book-actions">
                            <button class="btn btn-primary" onclick="showPage('book-detail')">查看详情</button>
                            <button class="btn btn-success member-only hidden" onclick="addToCart(3)">加入购物车</button>
                        </div>
                    </div>
                </div>
                
                <div class="book-card">
                    <div class="book-image">图书封面</div>
                    <div class="book-info">
                        <h3 class="book-title">三体</h3>
                        <p class="book-author">作者: 刘慈欣</p>
                        <p class="book-price">¥49.00</p>
                        <div class="book-actions">
                            <button class="btn btn-primary" onclick="showPage('book-detail')">查看详情</button>
                            <button class="btn btn-success member-only hidden" onclick="addToCart(4)">加入购物车</button>
                        </div>
                    </div>
                </div>
                
                <div class="book-card">
                    <div class="book-image">图书封面</div>
                    <div class="book-info">
                        <h3 class="book-title">人类简史</h3>
                        <p class="book-author">作者: 尤瓦尔·赫拉利</p>
                        <p class="book-price">¥68.00</p>
                        <div class="book-actions">
                            <button class="btn btn-primary" onclick="showPage('book-detail')">查看详情</button>
                            <button class="btn btn-success member-only hidden" onclick="addToCart(5)">加入购物车</button>
                        </div>
                    </div>
                </div>
                
                <div class="book-card">
                    <div class="book-image">图书封面</div>
                    <div class="book-info">
                        <h3 class="book-title">百年孤独</h3>
                        <p class="book-author">作者: 加西亚·马尔克斯</p>
                        <p class="book-price">¥55.00</p>
                        <div class="book-actions">
                            <button class="btn btn-primary" onclick="showPage('book-detail')">查看详情</button>
                            <button class="btn btn-success member-only hidden" onclick="addToCart(6)">加入购物车</button>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- 图书详情 -->
        <section id="book-detail" class="page hidden">
            <button class="btn btn-primary" onclick="showPage('books')" style="margin-bottom: 1rem;">返回图书列表</button>
            
            <div style="display: flex; gap: 2rem; background-color: white; padding: 2rem; border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.1);">
                <div style="flex: 1;">
                    <div style="height: 400px; background-color: #eee; display: flex; align-items: center; justify-content: center; color: #777;">图书封面</div>
                </div>
                
                <div style="flex: 2;">
                    <h1 style="font-size: 1.8rem; margin-bottom: 1rem;">JavaScript高级程序设计</h1>
                    <p style="color: #7f8c8d; margin-bottom: 0.5rem;">作者: Nicholas C. Zakas</p>
                    <p style="color: #7f8c8d; margin-bottom: 0.5rem;">出版社: 人民邮电出版社</p>
                    <p style="color: #7f8c8d; margin-bottom: 0.5rem;">ISBN: 9787115275790</p>
                    <p style="font-size: 1.5rem; color: #e74c3c; font-weight: bold; margin: 1.5rem 0;">¥89.00</p>
                    
                    <div style="margin: 2rem 0;">
                        <h3 style="margin-bottom: 0.5rem;">图书简介</h3>
                        <p>本书是JavaScript技术经典名著，全面深入地介绍了JavaScript开发者必须掌握的前端开发技术，涉及JavaScript的基础特性和高级特性。书中详尽讨论了JavaScript的各个方面，从JavaScript的起源开始，逐步讲解到实现复杂的Web应用。</p>
                    </div>
                    
                    <div class="book-actions">
                        <button class="btn btn-primary" style="margin-right: 1rem;">加入收藏</button>
                        <button class="btn btn-success member-only hidden" onclick="addToCart(1)">加入购物车</button>
                    </div>
                </div>
            </div>
        </section>

        <!-- 登录页面 -->
        <section id="login" class="page hidden">
            <h1 class="page-title">用户登录</h1>
            
            <form id="login-form" onsubmit="login(event)">
                <div class="form-group">
                    <label for="login-username">用户名</label>
                    <input type="text" id="login-username" required>
                </div>
                
                <div class="form-group">
                    <label for="login-password">密码</label>
                    <input type="password" id="login-password" required>
                </div>
                
                <button type="submit" class="btn btn-primary">登录</button>
                <button type="button" class="btn" onclick="showPage('home')" style="margin-left: 1rem;">取消</button>
            </form>
            
            <p>还没有账号？<a href="#" onclick="showPage('register')">立即注册</a></p>
        </section>

        <!-- 注册页面 -->
        <section id="register" class="page hidden">
            <h1 class="page-title">用户注册</h1>
            
            <form id="register-form" onsubmit="register(event)">
                <div class="form-group">
                    <label for="register-username">用户名</label>
                    <input type="text" id="register-username" required>
                </div>
                
                <div class="form-group">
                    <label for="register-password">密码</label>
                    <input type="password" id="register-password" required>
                </div>
                
                <div class="form-group">
                    <label for="register-confirm-password">确认密码</label>
                    <input type="password" id="register-confirm-password" required>
                </div>
                
                <div class="form-group">
                    <label for="register-email">电子邮箱</label>
                    <input type="email" id="register-email" required>
                </div>
                
                <div class="form-group">
                    <label for="register-phone">手机号码</label>
                    <input type="tel" id="register-phone" required>
                </div>
                
                <button type="submit" class="btn btn-primary">注册</button>
                <button type="button" class="btn" onclick="showPage('home')" style="margin-left: 1rem;">取消</button>
            </form>
            
            <p>已有账号？<a href="#" onclick="showPage('login')">立即登录</a></p>
        </section>

        <!-- 我的订单 -->
        <section id="orders" class="page hidden">
            <h1 class="page-title">我的订单</h1>
            
            <div class="tab-buttons">
                <button class="tab-btn active" onclick="changeOrderTab('all')">全部订单</button>
                <button class="tab-btn" onclick="changeOrderTab('unpaid')">待付款</button>
                <button class="tab-btn" onclick="changeOrderTab('paid')">已付款</button>
                <button class="tab-btn" onclick="changeOrderTab('shipped')">已发货</button>
                <button class="tab-btn" onclick="changeOrderTab('completed')">已完成</button>
            </div>
            
            <div class="order-list">
                <table>
                    <thead>
                        <tr>
                            <th>订单号</th>
                            <th>图书名称</th>
                            <th>数量</th>
                            <th>总价</th>
                            <th>状态</th>
                            <th>操作</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>ORD20230001</td>
                            <td>JavaScript高级程序设计</td>
                            <td>1</td>
                            <td>¥89.00</td>
                            <td>已付款</td>
                            <td>
                                <button class="btn btn-primary">查看详情</button>
                            </td>
                        </tr>
                        <tr>
                            <td>ORD20230002</td>
                            <td>Python编程：从入门到实践</td>
                            <td>2</td>
                            <td>¥150.00</td>
                            <td>已完成</td>
                            <td>
                                <button class="btn btn-primary">查看详情</button>
                            </td>
                        </tr>
                        <tr>
                            <td>ORD20230003</td>
                            <td>活着</td>
                            <td>1</td>
                            <td>¥39.00</td>
                            <td>待付款</td>
                            <td>
                                <button class="btn btn-primary">查看详情</button>
                                <button class="btn btn-success" style="margin-left: 0.5rem;">去支付</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </section>

        <!-- 购物车 -->
        <section id="cart" class="page hidden">
            <h1 class="page-title">购物车</h1>
            
            <div class="order-list">
                <table>
                    <thead>
                        <tr>
                            <th>图书封面</th>
                            <th>图书名称</th>
                            <th>单价</th>
                            <th>数量</th>
                            <th>小计</th>
                            <th>操作</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td><div style="width: 50px; height: 50px; background-color: #eee;"></div></td>
                            <td>JavaScript高级程序设计</td>
                            <td>¥89.00</td>
                            <td>
                                <input type="number" value="1" min="1" style="width: 60px; text-align: center;">
                            </td>
                            <td>¥89.00</td>
                            <td>
                                <button class="btn btn-danger">删除</button>
                            </td>
                        </tr>
                        <tr>
                            <td><div style="width: 50px; height: 50px; background-color: #eee;"></div></td>
                            <td>Python编程：从入门到实践</td>
                            <td>¥75.00</td>
                            <td>
                                <input type="number" value="2" min="1" style="width: 60px; text-align: center;">
                            </td>
                            <td>¥150.00</td>
                            <td>
                                <button class="btn btn-danger">删除</button>
                            </td>
                        </tr>
                    </tbody>
                    <tfoot>
                        <tr>
                            <td colspan="4" style="text-align: right;">总计：</td>
                            <td colspan="2">¥239.00</td>
                        </tr>
                    </tfoot>
                </table>
                
                <div style="text-align: right; margin-top: 2rem;">
                    <button class="btn btn-primary" style="margin-right: 1rem;">继续购物</button>
                    <button class="btn btn-success">去结算</button>
                </div>
            </div>
        </section>

        <!-- 图书管理 -->
        <section id="manage" class="page hidden">
            <h1 class="page-title">图书管理</h1>
            
            <div class="admin-actions">
                <button class="btn btn-primary" onclick="showAddBookForm()">添加新书</button>
            </div>
            
            <div class="order-list">
                <table>
                    <thead>
                        <tr>
                            <th>图书ID</th>
                            <th>图书封面</th>
                            <th>图书名称</th>
                            <th>作者</th>
                            <th>价格</th>
                            <th>库存</th>
                            <th>操作</th>
                        </tr>
                    </thead>
                    <tbody>
                        <tr>
                            <td>1</td>
                            <td><div style="width: 50px; height: 50px; background-color: #eee;"></div></td>
                            <td>JavaScript高级程序设计</td>
                            <td>Nicholas C. Zakas</td>
                            <td>¥89.00</td>
                            <td>100</td>
                            <td>
                                <button class="btn btn-primary">编辑</button>
                                <button class="btn btn-danger" style="margin-left: 0.5rem;">删除</button>
                            </td>
                        </tr>
                        <tr>
                            <td>2</td>
                            <td><div style="width: 50px; height: 50px; background-color: #eee;"></div></td>
                            <td>Python编程：从入门到实践</td>
                            <td>Eric Matthes</td>
                            <td>¥75.00</td>
                            <td>85</td>
                            <td>
                                <button class="btn btn-primary">编辑</button>
                                <button class="btn btn-danger" style="margin-left: 0.5rem;">删除</button>
                            </td>
                        </tr>
                        <tr>
                            <td>3</td>
                            <td><div style="width: 50px; height: 50px; background-color: #eee;"></div></td>
                            <td>活着</td>
                            <td>余华</td>
                            <td>¥39.00</td>
                            <td>120</td>
                            <td>
                                <button class="btn btn-primary">编辑</button>
                                <button class="btn btn-danger" style="margin-left: 0.5rem;">删除</button>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
            
            <!-- 添加图书表单 -->
            <div id="add-book-form" class="hidden" style="margin-top: 2rem;">
                <h2 style="margin-bottom: 1.5rem;">添加新书</h2>
                <form>
                    <div class="form-group">
                        <label for="book-title">图书名称</label>
                        <input type="text" id="book-title" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="book-author">作者</label>
                        <input type="text" id="book-author" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="book-isbn">ISBN</label>
                        <input type="text" id="book-isbn" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="book-price">价格</label>
                        <input type="number" id="book-price" min="0" step="0.01" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="book-stock">库存</label>
                        <input type="number" id="book-stock" min="0" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="book-publisher">出版社</label>
                        <input type="text" id="book-publisher" required>
                    </div>
                    
                    <div class="form-group">
                        <label for="book-image">封面图片</label>
                        <input type="file" id="book-image">
                    </div>
                    
                    <div class="form-group">
                        <label for="book-description">图书简介</label>
                        <textarea id="book-description" required></textarea>
                    </div>
                    
                    <button type="submit" class="btn btn-primary">保存</button>
                    <button type="button" class="btn" onclick="hideAddBookForm()" style="margin-left: 1rem;">取消</button>
                </form>
            </div>
        </section>

        <!-- 关于我们 -->
        <section id="about" class="page hidden">
            <h1 class="page-title">关于我们</h1>
            
            <div style="background-color: white; padding: 2rem; border-radius: 8px; box-shadow: 0 2px 10px rgba(0,0,0,0.1);">
                <h2 style="margin-bottom: 1rem;">吾书网络书店</h2>
                <p style="margin-bottom: 1.5rem;">吾书成立于2025年，是一家专注于图书销售的在线书店。我们致力于为读者提供最优质的图书和最便捷的购书体验。</p>
                
                <h3 style="margin-bottom: 1rem;">我们的使命</h3>
                <p style="margin-bottom: 1.5rem;">让阅读更简单，让知识更易得。我们希望通过我们的平台，能够让更多人爱上阅读，享受阅读带来的乐趣。</p>
                
                <h3 style="margin-bottom: 1rem;">联系我们</h3>
                <p style="margin-bottom: 0.5rem;">电话：888-888-8888</p>
                <p style="margin-bottom: 0.5rem;">邮箱：dontcallme@wushu.com</p>
                <p>地址：冰岛</p>
            </div>
        </section>
    </main>

    <footer>
        <div class="container">
            <p>&copy; 2023 吾书网络书店 版权所有</p>
        </div>
    </footer>

    <script>
        // 当前用户状态
        let currentUser = null;
        
        // 显示页面函数
        function showPage(pageId) {
            // 隐藏所有页面
            document.querySelectorAll('.page').forEach(page => {
                page.classList.remove('active');
                page.classList.add('hidden');
            });
            
            // 显示选中的页面
            const page = document.getElementById(pageId);
            if (page) {
                page.classList.remove('hidden');
                page.classList.add('active');
            }
            
            // 滚动到顶部
            window.scrollTo(0, 0);
        }
        
        // 登录函数
        function login(event) {
            event.preventDefault();
            
            const username = document.getElementById('login-username').value;
            const password = document.getElementById('login-password').value;
            
            // 模拟登录验证
            if (username && password) {
                currentUser = {
                    username: username,
                    isAdmin: username === 'admin' // 模拟管理员
                };
                
                updateUserUI();
                showPage('home');
                
                // 清空表单
                document.getElementById('login-form').reset();
            } else {
                alert('请输入用户名和密码');
            }
        }
        
        // 注册函数
        function register(event) {
            event.preventDefault();
            
            const username = document.getElementById('register-username').value;
            const password = document.getElementById('register-password').value;
            const confirmPassword = document.getElementById('register-confirm-password').value;
            const email = document.getElementById('register-email').value;
            const phone = document.getElementById('register-phone').value;
            
            // 简单验证
            if (password !== confirmPassword) {
                alert('两次输入的密码不一致');
                return;
            }
            
            if (username && password && email && phone) {
                // 模拟注册成功
                alert('注册成功！请登录');
                showPage('login');
                
                // 清空表单
                document.getElementById('register-form').reset();
            } else {
                alert('请填写所有必填字段');
            }
        }
        
        // 退出登录
        function logout() {
            currentUser = null;
            updateUserUI();
            showPage('home');
        }
        
        // 更新用户界面状态
        function updateUserUI() {
            const authButtons = document.getElementById('auth-buttons');
            const userInfo = document.getElementById('user-info');
            const memberOrdersLink = document.getElementById('member-orders-link');
            const adminManageLink = document.getElementById('admin-manage-link');
            const memberOnlyElements = document.querySelectorAll('.member-only');
            
            if (currentUser) {
                authButtons.classList.add('hidden');
                userInfo.classList.remove('hidden');
                document.getElementById('username-display').textContent = currentUser.username;
                
                // 显示会员订单链接
                memberOrdersLink.classList.remove('hidden');
                
                // 显示会员专属按钮
                memberOnlyElements.forEach(el => el.classList.remove('hidden'));
                
                // 如果是管理员，显示管理链接
                if (currentUser.isAdmin) {
                    adminManageLink.classList.remove('hidden');
                } else {
                    adminManageLink.classList.add('hidden');
                }
            } else {
                authButtons.classList.remove('hidden');
                userInfo.classList.add('hidden');
                memberOrdersLink.classList.add('hidden');
                adminManageLink.classList.add('hidden');
                
                // 隐藏会员专属按钮
                memberOnlyElements.forEach(el => el.classList.add('hidden'));
            }
        }
        
        // 添加购物车
        function addToCart(bookId) {
            if (!currentUser) {
                showPage('login');
                return;
            }
            
            alert('已添加到购物车');
            // 这里可以添加实际的购物车逻辑
        }
        
        // 切换订单标签页
        function changeOrderTab(tab) {
            // 更新按钮状态
            document.querySelectorAll('.tab-buttons .tab-btn').forEach(btn => {
                btn.classList.remove('active');
            });
            event.target.classList.add('active');
            
            // 这里可以添加实际的标签页切换逻辑
            console.log('切换到标签页:', tab);
        }
        
        // 显示添加图书表单
        function showAddBookForm() {
            document.getElementById('add-book-form').classList.remove('hidden');
        }
        
        // 隐藏添加图书表单
        function hideAddBookForm() {
            document.getElementById('add-book-form').classList.add('hidden');
        }
        
        // 初始化页面
        document.addEventListener('DOMContentLoaded', function() {
            updateUserUI();
            showPage('home');
        });
    </script>
</body>
</html>
