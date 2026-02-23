# BaseMetas Fileview Contributing Guide

我们非常欢迎社区的开发者向 BaseMetas Fileview 做出贡献。在提交贡献之前，请花一些时间阅读以下内容，保证贡献是符合规范并且能帮助到社区。

## Pull Request 贡献指南

### 1. 环境准备

> 需要安装 [Node.js 24](https://nodejs.org/en/) 和 [Docker](https://www.docker.com/)

首先把 fileview 仓库 fork 一份到自己的 Github，然后从个人仓库把项目 clone 到本地，项目默认是 `main` 分支。

然后依次在项目根目录运行以下命令：

```bash
# clone 代码，包含子仓库
git clone --recurse-submodules https://github.com/your/fileview.git

# 使用容器启动服务端开发环境，需要先安装并启动 docker 服务
cd fileview-backend
docker compose up
docker exec -it fileview-backend /bin/bash

# 以上也可以在 IDE 中启动开发环境，如 vscode
# vscode 中打开服务端项目根目录，点击左下角"在容器中重新打开"

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

运行完上述命令后，环境已经准备好，此时可以新拉一条分支进行开发。

### 2. 开发与调试

Fileview 项目采用前后端分离架构，主要包含两个模块：

- **fileview-frontend**：前端项目，使用 React + TypeScript + Vite
- **fileview-backend**：后端项目，使用 Spring Boot + Java
  - **fileview-preview**：预览服务模块
  - **fileview-convert**：转换服务模块

开发者可以单独运行或调试特定模块：

```bash
# 后端开发模式启动预览服务
./start-preview.sh

# 后端开发模式启动转换服务
./start-convert.sh

# 前端开发模式启动
npm run dev
```

开发过程中，可以在 IDE 中分别打开前端和后端项目进行断点调试。对于前端，可以使用浏览器开发者工具进行调试；对于后端，可以使用 IntelliJ IDEA 或其他 Java IDE 进行断点调试。

### 3. 技术栈与依赖管理

项目使用的技术栈：

- 前端：React, TypeScript, Vite, Ant Design
- 后端：Spring Boot 3.x, Java 17+, Maven
- 数据库：Redis（缓存）, RocketMQ（消息队列）
- 构建工具：Maven（后端）, npm（前端）

新增或修改依赖时，请注意：

- 前端依赖在 `fileview-frontend/package.json` 中管理
- 后端依赖在 `fileview-backend/pom.xml` 及各子模块的 pom.xml 中管理
- 修改依赖后确保所有构建和测试都能正常通过

```bash
# 前端安装依赖
npm install <package-name>

# 后端添加依赖（修改 pom.xml 文件）
./mvnw clean compile
```

### 4. 单元测试

项目包含前端和后端的单元测试：

```bash
# 运行前端测试
npm run test

# 运行后端测试
./mvnw test

# 运行特定模块的测试
./mvnw test -pl fileview-preview
./mvnw test -pl fileview-convert
```

提交代码前，请确保所有相关测试能够通过。如果添加了新功能，请相应地添加单元测试。

### 5. 代码风格

- 前端代码遵循 ESLint 和 Prettier 规范
- 后端代码遵循 Google Java Style Guide
- 提交前请运行代码格式化工具

```bash
# 前端代码格式化
npm run lint
npm run format

# 后端代码格式化（如有配置）
./mvnw spotless:apply
```

### 6. 提交 commit

仓库遵从 [Conventional Commits](https://www.conventionalcommits.org/) 规范，在输入 commit message 的时候请务必遵从此规范。

常见类型包括：
- feat: 新功能
- fix: 修复 bug
- docs: 文档更新
- style: 代码格式调整
- refactor: 重构
- test: 测试相关
- chore: 其他杂项

### 7. 提交 Pull Request

> 如果对 PR（Pull Request）不了解，请阅读 [《关于拉取请求》](https://docs.github.com/zh/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests)

完成开发后，推送到自己的仓库，就可以准备提交 Pull Request 了。

提交 PR 前请阅读以下注意事项：

1. 保证 `npm run build`（前端）和 `./mvnw clean package`（后端）能够编译成功
2. 保证代码能通过 ESLint 和代码检查
3. 保证所有相关测试用例都能够通过
4. 为新功能或修改添加适当的测试用例
5. 保证 commit 信息需要遵循 [Conventional Commits](https://www.conventionalcommits.org/) 规范
6. 如果提交的代码很多或功能复杂，建议分成多个相关的 commit 提交
7. 更新相关文档（如果需要）
8. 需要先从主仓库 main 分支合并最新代码并解决冲突

### 8. 本地开发最佳实践

- 启动后端服务（预览和转换服务）后再启动前端服务
- 使用 Docker Compose 进行本地开发环境搭建
- 对于复杂的文件格式支持，可在开发环境中进行端到端测试
- 修改配置文件后记得重启对应的服务

### 9. 文档

当提交涉及新增特性、重要修改或 API 变更时，请及时新增、修改对应的文档。

- API 文档通常在 `fileview-backend` 模块中的 README
- 配置说明在相应模块的 README 中
- 使用示例和教程在项目根目录的文档中
