---
description: 'https://git.oa.com/raft/raft-microservice-template-go'
---

# 实践：RAFT微服务组件开发模板

### 目录 <a id="%E7%9B%AE%E5%BD%95"></a>

* [👑 项目特点](data:text/html;charset=utf-8,%3C%21DOCTYPE%20html%3E%0D%0A%3Chtml%20lang%3D%22en%22%20style%3D%22width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3Chead%3E%0D%0A%09%3Ctitle%3EVirtual%20Document%3C%2Ftitle%3E%0D%0A%3C%2Fhead%3E%0D%0A%3Cbody%20style%3D%22margin%3A%200%3B%20overflow%3A%20hidden%3B%20width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3C%2Fbody%3E%0D%0A%3C%2Fhtml%3E#crown-%E9%A1%B9%E7%9B%AE%E7%89%B9%E7%82%B9)
* [✈️ 快速开始](data:text/html;charset=utf-8,%3C%21DOCTYPE%20html%3E%0D%0A%3Chtml%20lang%3D%22en%22%20style%3D%22width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3Chead%3E%0D%0A%09%3Ctitle%3EVirtual%20Document%3C%2Ftitle%3E%0D%0A%3C%2Fhead%3E%0D%0A%3Cbody%20style%3D%22margin%3A%200%3B%20overflow%3A%20hidden%3B%20width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3C%2Fbody%3E%0D%0A%3C%2Fhtml%3E#airplane-%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B)
* [📂 目录结构](data:text/html;charset=utf-8,%3C%21DOCTYPE%20html%3E%0D%0A%3Chtml%20lang%3D%22en%22%20style%3D%22width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3Chead%3E%0D%0A%09%3Ctitle%3EVirtual%20Document%3C%2Ftitle%3E%0D%0A%3C%2Fhead%3E%0D%0A%3Cbody%20style%3D%22margin%3A%200%3B%20overflow%3A%20hidden%3B%20width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3C%2Fbody%3E%0D%0A%3C%2Fhtml%3E#open_file_folder-%E7%9B%AE%E5%BD%95%E7%BB%93%E6%9E%84)
* [💻 基本命令](data:text/html;charset=utf-8,%3C%21DOCTYPE%20html%3E%0D%0A%3Chtml%20lang%3D%22en%22%20style%3D%22width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3Chead%3E%0D%0A%09%3Ctitle%3EVirtual%20Document%3C%2Ftitle%3E%0D%0A%3C%2Fhead%3E%0D%0A%3Cbody%20style%3D%22margin%3A%200%3B%20overflow%3A%20hidden%3B%20width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3C%2Fbody%3E%0D%0A%3C%2Fhtml%3E#computer-%E5%9F%BA%E6%9C%AC%E5%91%BD%E4%BB%A4)
* [💡 服务实现](data:text/html;charset=utf-8,%3C%21DOCTYPE%20html%3E%0D%0A%3Chtml%20lang%3D%22en%22%20style%3D%22width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3Chead%3E%0D%0A%09%3Ctitle%3EVirtual%20Document%3C%2Ftitle%3E%0D%0A%3C%2Fhead%3E%0D%0A%3Cbody%20style%3D%22margin%3A%200%3B%20overflow%3A%20hidden%3B%20width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3C%2Fbody%3E%0D%0A%3C%2Fhtml%3E#bulb-%E6%9C%8D%E5%8A%A1%E5%AE%9E%E7%8E%B0)
* [🚢 集成部署](data:text/html;charset=utf-8,%3C%21DOCTYPE%20html%3E%0D%0A%3Chtml%20lang%3D%22en%22%20style%3D%22width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3Chead%3E%0D%0A%09%3Ctitle%3EVirtual%20Document%3C%2Ftitle%3E%0D%0A%3C%2Fhead%3E%0D%0A%3Cbody%20style%3D%22margin%3A%200%3B%20overflow%3A%20hidden%3B%20width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3C%2Fbody%3E%0D%0A%3C%2Fhtml%3E#ship-%E9%9B%86%E6%88%90%E9%83%A8%E7%BD%B2)
* [❓ Q & A](data:text/html;charset=utf-8,%3C%21DOCTYPE%20html%3E%0D%0A%3Chtml%20lang%3D%22en%22%20style%3D%22width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3Chead%3E%0D%0A%09%3Ctitle%3EVirtual%20Document%3C%2Ftitle%3E%0D%0A%3C%2Fhead%3E%0D%0A%3Cbody%20style%3D%22margin%3A%200%3B%20overflow%3A%20hidden%3B%20width%3A%20100%25%3B%20height%3A%20100%25%22%3E%0D%0A%3C%2Fbody%3E%0D%0A%3C%2Fhtml%3E#question-q--a)

### 👑 项目特点 <a id="crown-%E9%A1%B9%E7%9B%AE%E7%89%B9%E7%82%B9"></a>

* 【五脏俱全的麻雀】仅有200行核心代码，提供快速开发、集成、调试、文档、与部署微服务所用到的各项能力。
* 【标准高效的接口】一套实现同时对外提供 gRPC、RESTfull 接口（后续支持tRPC），实现过程类似“填空题”。
* 【清晰易懂的代码】集成 swagger-ui，用户在定义接口后自动生成接口文档和调试工具。
* 【内部资源的集成】整合STEK、OCI、企业微信等腾讯内公司资源

如果你想尽快了解一下项目， 也可以点击这个地址在STKE上体验：[DEMO 在线体验](http://9.148.192.215/)

### ✈️ 快速开始 <a id="airplane-%E5%BF%AB%E9%80%9F%E5%BC%80%E5%A7%8B"></a>

先将git库拉取到本地

```text
git clone http://git.code.oa.com/raft/raft-microservice-template-go.git
cd raft-microservice-template-go
```

启动并微服务仅需在命令行中简单执行

```text
# 或 make run
make
```

在浏览器中打开 [http://127.0.0.1:8811](http://127.0.0.1:8811/) 即可查看接口文档并调试接口  
（远程服务器上需将127.0.0.1改为实际服务器的地址）。

### 📂 目录结构 <a id="open_file_folder-%E7%9B%AE%E5%BD%95%E7%BB%93%E6%9E%84"></a>

```text
.
├── main.go         # 入口文件
├── Makefile        # 构建文件
├── proto
│   └── proto.proto # 协议文件，定义所需要的gRPC和REST接口
├── server
│   ├── framework.go
│   └── server.go   # 服务实现，实现gRPC和REST服务
├── .orange-ci.yml  # 持续集成文件， 用于部署项目到STKE
├── ...
├── ...
└── third_party
    └── OpenAPI     # swagger-ui 用于文档展示和接口调试
```

### 💻 基本命令 <a id="computer-%E5%9F%BA%E6%9C%AC%E5%91%BD%E4%BB%A4"></a>

本模板工程使用Makefile构建工程，具体可以打开并参考工程根目录下的Makefile文件  
在工程根目录下，执行如下命令可以构建并启动服务

**1. 构建并启动服务**

```text
# 或 make run
make
```

**2. 仅构建工程（并生成协议和文档）**

```text
make build
```

**3. 仅运行工程**

```text
go run main.go
```

**4. 仅生成协议和文档**

```text
make generate
```

**5. 生成docker镜像**

```text
make docker
```

### 💡 服务实现 <a id="bulb-%E6%9C%8D%E5%8A%A1%E5%AE%9E%E7%8E%B0"></a>

**STEP 1. 修改proto.proto文件**  
在proto.proto文件中增加接口

```text
service UserService {
 
    rpc AddUser(AddUserRequest) returns (User) {
      option (google.api.http) = {
        // Route to this method from POST requests to /api/v1/users
        post: "/api/v1/users"
        body: "*"
      };
      option (grpc.gateway.protoc_gen_swagger.options.openapiv2_operation) = {
        summary: "增加一个用户"
        description: "向数据库中增加一个用户."
        tags: "Users"
      };
    }
}
```

**STEP 2. 编译gRPC接口文件**

```text
make generate
```

**STEP 3. 修改gRPC注册代码**  
生成完gRPC协议后， 还需要根据服务的名字修改少量的服务注册代码。

在framework.go中有如下两句需要修改，修改成对应的服务名称。  
如 SafeService 改成 RegisterSafeServiceServer

```text
func ListenAndServeGRPC(address string) error {
	...
	proto.RegisterUserServiceServer(grpcServer, &s)
    ...
}

func ListenAndServeREST(restAddress, grpcAddress string, swagger_ui bool) error {
    ...
	err := proto.RegisterUserServiceHandlerFromEndpoint(
		ctx,
		mux,
		grpcAddress,
		opts,
	)
    ...
}
```

**STEP 4. 实现服务**  
在 server.go 文件中添加服务的实现代码

```text
type Server struct{}

func (b *Server)DelUser(context.Context, *proto.DelUserRequest) (*proto.DelUserResponse, error){
	return &proto.DelUserResponse{}, nil
}


func (b *Server) AddUser(ctx context.Context, _ *proto.AddUserRequest) (*proto.User, error) {
	return &proto.User{}, nil
}

func (b *Server) ListUsers(_ *proto.ListUsersRequest, srv proto.UserService_ListUsersServer) error {
	return nil
}


```

**STEP 5. 启动服务**

```text
# 或 make run
make
```

在浏览器中打开 [http://127.0.0.1:8811](http://127.0.0.1:8811/) 即可查看接口文档并调试接口  
（远程服务器上需将127.0.0.1改为实际服务器的地址）。

### 🚢 集成部署 <a id="ship-%E9%9B%86%E6%88%90%E9%83%A8%E7%BD%B2"></a>

项目中目前已经集成了Docker和OCI，并只需简单配置后提交代码，既可以在STKE上部署项目。

**STEP 1. GIT仓库授权**  
描述了当仓库发生一些事件时，`Orange-ci` 应该如何去进行处理。  
因此 `Orange-ci`工具需要使用git仓库授权，点击下面链接进行授权：  
[OAuth2 授权](http://orange-ci.oa.com/oauth/authorize)

**STEP 2. 增加修改OCI配置文件**  
通常，约定配置文件命名为 `.orange-ci.yml`，此文件已经编写好，并放置在了工程目录下。

大部分信息已经配置好了， 开发者可以简单的填写如下几项

```text
  # 更新 stke
  - name: stke update
    type: stke:update
    options:
      kind: deployment
      projectName: XXXX  ## 这里修改成STKE上的 工程名字
      namespaces: XXXX   ## 这里修改成STKE上的 名字空间
      clusterId: XXXX    ## 这里修改成STKE上的 集群ID
      resourceIns: XXXX  ## 这里修改成STKE上的 资源实例
      name: demo-container
```

如下两个标签的地址可以改成自己申请的docker进项的存储地址（简单测试也可以不改）

```text
  # 创建两个标签，多出一个作为历史版本
  - name: create DOCKER_LATEST_TAG
    script: echo -n csighub.tencentyun.com/raft/raft-microservice-demo:latest
    envExport:
      info: DOCKER_LATEST_TAG
  - name: create DOCKER_TIME_TAG
    script: echo -n csighub.tencentyun.com/raft/raft-microservice-demo:$(date "+%Y%m%d%H%M")
    envExport:
      info: DOCKER_TIME_TAG
```

**STEP 3. 提交代码， 触发自动构建**  
之后提交代码。 构建将自动开始， 并部署到STKE。  
部署和构建过程会由企业微信通知到你。

### ❓ Q & A <a id="question-q-a"></a>

Q&A 暂时还没有实现编写， 如果遇到任何问题，请当面找理查德解决。🐷

