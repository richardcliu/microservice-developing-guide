# 三、gRPC接口的实现

## 为什么使用 gRPC?

gRPC是一个高性能、通用的开源RPC框架，其由Google主要面向移动应用开发并基于HTTP/2协议标准而设计，基于ProtoBuf\(Protocol Buffers\)序列化协议开发，且支持众多开发语言。gRPC提供了一种简单的方法来精确地定义服务和为iOS、Android和后台支持服务自动生成可靠性很强的客户端功能库。

![](../.gitbook/assets/grpc_concept_diagram_00.png)

使用grpc的优点很多，支持**多种语言**，**二进制的数据**可以加快传输速度，**基于http2的多路复用**可以减少服务之间的连接次数，和**函数一样的调用方式**也有效的提升了开发效率。

## 准备工作

要通过go语言开发gRPC的接口，需要一些准备工作：

**STEP 1：** 先安装`grpc-go 的库，在bash中执行如下命令即可`

```go
go get google.golang.org/grpc
```

**STEP 2：**安装Protocol Buffer V3

去[https://github.com/google/protobuf/releases](https://github.com/google/protobuf/releases)下载最新的稳定的版本  
然后解压缩，把里面的文件放到`$PATH`中。

除了手动下载PB的release版本之外，Mac用户可以通过brew来安装：

```bash
# mac用户可以用brew安装
brew install protobuf

# 安装完成后可以看一下版本。 3.0版本以上才可以哦~
protoc --version
```

**STEP 3：**安装go的grpc插件

```go
go get -u -v github.com/golang/protobuf/proto
go get -u -v github.com/golang/protobuf/protoc-gen-go
```

## 定义服务

gRPC通过pb协议文件来定义服务，因此我们需要使用protocol buffer去定义service、request和response的类型。这里我们创建一个protos目录并在其中新建一个helloworld.proto文件，加入如下代码：

```c
syntax = "proto3";
package helloworld;

// 定义 Greeter 服务
service Greeter{
    rpc SayHello (HelloRequest) returns (HelloResponse){}
}

// 请求 Request
message HelloRequest{
    string name = 1;
}
// //响应 Response
message HelloResponse{
    string message = 1;
}
```

之后使用如下命令则可以生成helloworld对应的go文件

```bash
protoc -I protos protos/helloworld.proto --go_out=plugins=grpc:protos  
```

{% hint style="warning" %}
注意执行上述命令所在的目录：

```bash
#. <-- 注意在这个位置（和protos同层）执行下述命令，这里执行的目录很重要
#└── protos
#    └── helloworld.proto
```
{% endhint %}

之后，你会发现protos目录下生成了一个名为helloworld.pb.go的文件， 这就是我们需要的目标文件了。

```bash
#└── protos
#    ├── helloworld.pb.go  <-- 这里得到了我们要的目标文件
#    └── helloworld.proto
```

打开生成的helloworld.pb.go文件， 我们可以找到如下接口的声明。稍后我们将在服务端程序中实现这一接口。

```go
type GreeterClient interface {
	SayHello(ctx context.Context, in *HelloRequest, opts ...grpc.CallOption) (*HelloResponse, error)
}
```

## 编写服务端代码

有了pb的协议之后，我们可以开始用go语言编写服务端代码了，我们新建一个greeter\_server/main.go文件。并将为其编写如下代码：

```go
package main

import (
	"context"
	pb "grpc/helloworld"
	"net"
	"log"
	"google.golang.org/grpc"
	"google.golang.org/grpc/reflection"
)

const port = ":50051"

//server 用于实现从proto 服务定义生成的 helloworld.GreeterServer接口.
type server struct {}

// SayHello 实现 helloworld.GreeterServer接口.
func (s *server)SayHello(context.Context, *HelloRequest) (*HelloResponse, error){
	return pb.HelloResponse{Message:"heelo" + in.Name}, nil
}

func main() {
	lis, err := net.Listen("tcp", port)
	if err != nil {
		log.Fatalf("failed to listen: %v", err)
	}

	//创建gRPC 服务器，将我们实现的Greeter服务绑定到一个端口
	s := grpc.NewServer()
	pb.RegisterGreeterServer(s, &server{})
	reflection.Register(s)
	if err := s.Serve(lis); err != nil {
		log.Fatalf("failed to server: %v", err)
	}
}
```

## 小结

* 在一个 .proto 文件内定义服务。
* 用 protocol buffer 编译器生成服务器和客户端代码。
* 使用 gRPC 的 Go API 为你的服务实现一个简单的客户端和服务器。

