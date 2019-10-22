# Q&A

## Q: 如何杀掉占用某端口的进程

#### 第一招:

```bash
kill -9 $(lsof -i tcp:XXXX -t)
```

#### 第二招:

```bash
fuser -k XXXX/tcp
```

记得把 xxxx 改成自己要杀掉的端口号哦~

## Q: 如何安装gocode、golint等代码提示插件？

 命令提示行中输入

```bash
go get -u -v github.com/nsf/gocode
go get -u -v github.com/rogpeppe/godef
go get -u -v github.com/golang/lint/golint
go get -u -v github.com/lukehoban/go-find-references
go get -u -v github.com/lukehoban/go-outline
go get -u -v sourcegraph.com/sqs/goreturns
go get -u -v golang.org/x/tools/cmd/gorename
go get -u -v github.com/tpng/gopkgs
go get -u -v github.com/newhook/go-symbols
```

下载过程中如果提示链接不上sourcegraph.com/sqs/goreturns的错误，则给cmd设置代理

```bash
set http_proxy=http://web-proxy.tencent.com:8080
set https_proxy=http://web-proxy.tencent.com:8080
```

## Q: Go 语言的对象是在堆上分配的还是在栈上分配的

简单回答，会有Go语言的编译器自动决定。开发者无需关心。  
[补充阅读：http://zenlife.tk/go-allocated-on-heap-or-stack.md](http://zenlife.tk/go-allocated-on-heap-or-stack.md)



