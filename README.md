# ubuntu-dev

此这个镜像配置了主流的C/C++包管理器和构建系统，以及了我所涉及到需要交叉编译的工具链，如果您有特殊的需要，可以自行添加相关环境，再进行构建和使用。

**构建镜像**

```bash
docker buildx build . -t ubuntu-dev/ubuntu22.04
```

**使用镜像**

```bash
docker run -itd -p 2201:22 --name dev ubuntu-dev/ubuntu22.04:latest
```

## 使用建议

### Tap1. Conan包管理数据持久化

在镜像中，使用Conan 作为包管理器。建议在创建容器时将 /root/.conan2 文件夹挂载到本地目录中。这些数据很重要，因为 Conan 会将已经下载和编译的库存放在这个文件夹内。如果没有做持久化，那么每次使用都将需要重新构建这些库。

### Tap2. 使用CLion

CLion 是一个非常好用的 IDE，功能多样且灵活。它默认使用 CMake 进行构建，并且对 CMake 的支持比其他 IDE 都要强大，配置项目和管理变得非常轻松。除此之外，CLion 还提供了 Conan 插件，可以通过 GUI 方式配置依赖，使用体验非常棒。另外，CLion 对 Docker 的支持也是一大亮点。启动速度极快，几乎感觉不到延迟，使用起来非常顺畅。这些特性让 CLion 成为开发 C++ 项目的理想选择。

致谢：jelin-sh/jelin-dev
