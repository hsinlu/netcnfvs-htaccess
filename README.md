#netcnfvs-htaccess

htaccess文件适用于万网的免费主机，让其支持PHP laravel框架和多网站。

#### 虚拟主机部署路径

```
/htdocs
    /logreport
    /streamlet
    /wizardlychars
    .htaccess
```

#### htaccess

```
# 开启重写
RewriteEngine on

# 顶级域名 hsinlu.com
RewriteCond %{HTTP_HOST} ^hsinlu.com$
RewriteCond %{REQUEST_URI} !^/streamlet/public/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ /streamlet/public/$1
RewriteCond %{HTTP_HOST} ^hsinlu.com$
RewriteRule ^(/)?$ /streamlet/public/index.php [L]

# 二级域名：streamlet.hsinlu.com 访问/streamlet/public
RewriteCond %{HTTP_HOST} ^streamlet.hsinlu.com$
RewriteCond %{REQUEST_URI} !^/streamlet/public/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ /streamlet/public/$1
RewriteCond %{HTTP_HOST} ^streamlet.hsinlu.com$
RewriteRule ^(/)?$ /streamlet/public/index.php [L]

# 二级域名：wizardlychars.hsinlu.com 访问/wizardlychars/public
RewriteCond %{HTTP_HOST} ^wizardlychars.hsinlu.com$
RewriteCond %{REQUEST_URI} !^/wizardlychars/public/
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^(.*)$ /wizardlychars/public/$1
RewriteCond %{HTTP_HOST} ^wizardlychars.hsinlu.com$
RewriteRule ^(/)?$ /wizardlychars/public/index.php [L]
```
