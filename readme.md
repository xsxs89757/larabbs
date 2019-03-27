## <center>larabbs</center>

## 1.安装laravel 应用

### 1)composer 安装 切换至packagist
#### composer config -g repo.packagist composer https://packagist.laravel-china.org
### 2)laravel 应用安装
#### composer create-project laravel/laravel larabbs --prefer-dist "5.5.*"
## 2.Git 代码版本控制
### 1)把新建的laravel项目那日git版本控制中
	git init
	git add -A
	git commit -m "初始化"
### 2)在github上面新建项目并将初始化代码推送至github(注意请把下面的 username 替换为你的用户名。)
	git remote add origin git@github.com:username/larabbs.git
	git push -u origin master //后面添加 -f 参数可以强制刷新线上库
##### git的基本设置 
###### Git 进行用户名和邮箱进行设置
		git config --global user.name "Your Name"
		git config --global user.email your@example.com
			解释： --global 选项代表对 Git 进行全局设置。
###### 接下来设置 Git 推送分支时相关配置
		git config --global push.default simple
###### GitHub 账号设置 SSH Key(使用git bash)
		ssh-keygen -t rsa -C "youname@example.com"
		eval ssh-agent -s
		ssh-agent bash
		ssh-add ~/.ssh/id_rsa //该步骤生成目录下面的.pub内容为publickey
		登录https://github.com/，在页面右上角自己头像右边箭头处右击，弹框中进入setting功能
		setting界面右边菜单选择SSH and GPG keys，选择新建SSH keys
## 3.配置信息
### 1.存放位置
	Laravel 框架的所有配置都保存在 config 目录中，每个文件中包含多个配置选项，每个选项都有说明。
	你可随时查看这些文件并熟悉都有哪些配置选项可供你使用。
###	2.配置文件
	下面是配置文件的简单说明：
	文件名称							配置类型
	app.php					应用相关，如项目名称、时区、语言等
	auth.php				用户授权，如用户登录、密码重置等
	broadcasting.php		事件广播系统相关配置
	cache.php				缓存相关配置
	database.php			数据库相关配置，包括 MySQL、Redis 等
	filesystems.php			文件存储相关配置
	mail.php				邮箱发送相关的配置
	queue.php				队列系统相关配置
	services.php			放置第三方服务配置
	session.php				用户会话相关配置
	view.php				视图存储路径相关配置
###	3.访问配置值
####	1.你可以在应用程序的任何位置使用全局 config 函数来访问配置值
		配置值的访问可以使用「点」语法，这其中包含了要访问的 文件名称 和 选项 的名称。
		还可以指定默认值，如果配置选项不存在，则返回默认值
		$value = config('app.timezone');
####	2.要在运行时设置配置值，传递一个数组给 config 函数
		config(['app.timezone' => 'America/Chicago']);
## 4.辅助函数
	Laravel 提供了很多 辅助函数，有时候我们也需要创建自己的辅助函数。
	我们把所有的『自定义辅助函数』存放于 bootstrap/helpers.php 文件中，这里需要新建一个空文件
	在 bootstrap/app.php 文件的最顶部进行加载：
	<?php
	require_once __DIR__ . '/helpers.php';
## 5. artisan  创建指令
### 1) 创建controller
	php artisan make:controller YourController
###	2)
## 6. 模板
###	1) 创建
	模板命名为template.blade.php (template改为你自己的模板名称)
###	2) 视图
	@include('') //包含模板
	@yield('key','defaultValue') //占位标记
	@extends('') //继承模板
	@section('key','yourValue') //填充占位符 第二个参数如果不填写职责需要@stop 结尾
	