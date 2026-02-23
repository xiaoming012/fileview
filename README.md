# BaseMetas Fileview 在线文件预览引擎

新一代通用型在线文件预览引擎，具有以下特点：
- 全格式覆盖，一套能力支撑所有文档场景
- 快速接入，轻量级开发
- 跨平台多终端适配
- 无外部依赖、零插件 

## 相关站点

- 官方文档 https://fileview.basemetas.cn
- 在线体验 https://file.basemetas.cn

## 开源地址

- https://github.com/basemetas/fileview

## 本地运行

```bash
# clone 代码，包含子仓库
git clone --recurse-submodules https://github.com/basemetas/fileview.git

# 使用容器启动服务端开发环境，需要先安装并启动 docker 服务
cd fileview-backend
docker compose up
docker exec -it fileview-backend /bin/bash

# 以上也可以在 IDE 中启动开发环境，如 vscode
# vscode 中打开服务端项目根目录，点击左下角“在容器中重新打开”

# 进入容器，启动预览服务和转换服务
cd /var/app/fileview-backend
chmod +x ./*.sh
./start-preview.sh
./start-convert.sh

# 安装并启动前端开发环境，需要先安装 nodejs LTS 版本，如 nodejs v24+
cd fileview-frontend
npm i
npm run dev

```

## 问题反馈与建议

在提 issue 前请确保满足以下条件：

- 必须是一个 bug 或者功能新增。
- 已经在 issue 中搜索过，并且没有找到相似的 issue 或者解决方案。
- 推荐使用 [bug-report](./bug-report.md) 模板提交 issus

> 强烈推荐阅读 [《如何向开源社区提问题》](https://github.com/seajs/seajs/issues/545) 和 [《如何有效地报告 Bug》](http://www.chiark.greenend.org.uk/%7Esgtatham/bugs-cn.html)、[《如何向开源项目提交无法解答的问题》](https://zhuanlan.zhihu.com/p/25795393)，更好的问题更容易获得帮助。

## 贡献指南
我们非常欢迎社区开发者为 BaseMetas Fileview 贡献代码，在贡献之前请先阅读[贡献指南](./CONTRIBUTING.md)。

如果你想为 BaseMetas Fileview 实现一个重要功能，需要先撰写 RFC 文档，按照 BaseMetas Fileview 的[RFC 机制](./rfcs.md) 进行操作，在经过社区讨论完善后才可以进行代码的提交。

## 用户交流群

