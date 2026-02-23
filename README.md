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

## 贡献指南

## 用户交流群

