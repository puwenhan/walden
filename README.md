# Walden 最适合东半球同学使用的文档框架

![](https://codeship.com/projects/e42f8850-50a5-0133-5daf-5abe51be460d/status?branch=master)

或许是极人性化的一个文档管理框架，让你一下子就喜欢上写文档分享，[官网主页](http://www.huamanshu.com/walden.html)了解更多。

## 演示
![walden](https://raw.github.com/meolu/Walden/master/static/screenshots/walden.gif)

体验[demo](http://walden.huamanshu.com/)。

## 特点

* Markdown语法
* 修改后实时展现，无编译
* 多模板支持
* 图片、附件上传，自动生成url
* 多项目
* 任意定义目录嵌套、定义文档，目录与文档均可中文（甚至推荐中文）
* 文档、图片、附件同步保存至git，这下你安心了吧

## 一、安装

零安装、零配置，无数据库，不需要composer，开箱即用。

* 依赖git，php5.3，nginx环境

## 二、快速开始
```php
vi Config.php
return [
    // 保存文档和附件的git ssh地址，可以是在github，好吧，不想公开，可以bitbucket
    ///php进程的用户的id_rsa.pub已添加到git的ssh-key。这样才可以推送markdown下的文件。
    'git' => 'git@github.com:meolu/Walden-markdown-demo.git',
];
```

## 自定义模板

前端同学可以自己定义模板，在templates下新建一个模板目录，包含预览模板：`markdown-detail-view.php`，编辑模板：`markdown-editor-view.php`，然后修改`Config.php`的`template`为你的模板项目。

最后，当然希望你可以给此项目提个pull request，目前只有一个bootstrap的默认模板：(


## to do list

* 文档搜索
* 文档删除，重命名UI化


## 四、可能会遇到的问题

### nginx简单配置

```
server {
    listen       80;
    server_name  Walden.dev;
    root /the/dir/of/Walden;
    index index.php;

    # 建议放内网做文档服务
    allow 192.168.0.0/24;
    deny all;

    location / {
        try_files $uri $uri/ /index.php$is_args$args;
    }

    location ~ \.php$ {
        try_files $uri =404;
        fastcgi_pass   127.0.0.1:9000;
        fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
        include        fastcgi_params;
    }
}
```

###上传文件提示413 Request Entity Too Large

```
修改nginx.conf的http模块：client_max_body_size 10m;
```

## CHANGELOG
瓦尔登的版本记录：[CHANGELOG](https://github.com/meolu/walden/blob/master/CHANGELOG.md)

## 有问题加群
**QQ：135114826**

