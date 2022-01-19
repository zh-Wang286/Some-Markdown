> 《每天5分钟玩转Docker容器技术》CloudMan

[toc]

## bind mount

`bind mount`是将`host`上已经存在的目录或文件`mount`到容器。

例如，`host`上有目录`$HOME/htdocs`

![image-20211027235915618](image-20211027235915618.png)

通过`-v`将其`mount`到`httpd`容器。`/usr/local/apache2/htdocs`就是 Apache Server 存取静态文件的地方。由于`/usr/local/apache2/htdocs`已经存在，原有的数据会被隐藏起来，取而代之的是 host`$HOME/htdocs/`中的数据

```bash
docker run -d -p 80:80 -v ~/htdocs:/usr/local/apache2/htdocs --name volumeTest httpd
# -v <host path>:<container path>
```

![image-20211028000333454](image-20211028000333454.png)

`curl`显示当前主页确实是`$HOME/htdocs/index.html`中的内容

![image-20211028000551501](image-20211028000551501.png)

更新一下内容，再次查看

```bash
echo "update index page" > ~/htdocs/index.html
```

![image-20211028000831684](image-20211028000831684.png)

`host`中的修改已经生效，`bind mount`可以让`host`与容器共享数据。

另外，`bind mount`时也可以指定数据的读写权限，默认是可读可写，可指定为只读

```bash
docker run -d -p 80:80 -v ~/htdocs:/usr/local/apache2/htdocs:ro --name volumeTest httpd
```

也可以单独指定一个文件

```bash
docker run -d -p 80:80 -v ~/htdocs/index.html:/usr/local/apache2/htdocs/new_index.html --name volumeTest httpd
```

使用 `bind mount` 单个文件的场景是:只需要向容器添加文件，不希望覆盖整个目录。在上面的例子中，我们将 html 文件加到 apache 中，同时也保留了容器原有的数据。
使用单一文件有一点要注意：`host` 中的源文件必须要存在，不然会当作一个新目录 `bind mount` 给容器。
`mount point` 有很多应用场景，比如我们可以将源代码目录 `mount` 到容器中，在 `host` 中修改代码就能看到应用的实时效果。再比如将 MySQL 容器的数据放在 `bind mount` 里，这样 host 可以方便地备份和迁移数据。
`bind mount` 的使用直观高效，易于理解，但它也有不足的地方：`bind mount` 需要指定 `host`文件系统的特定路径，这就限制了容器的可移植性，当需要将容器迁移到其他 `host`，而该 `host`没有要 `mount` 的数据或者数据不在相同的路径时，操作会失败。