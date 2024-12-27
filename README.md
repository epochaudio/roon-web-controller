# Roon Album Art 显示器

优雅的 Roon 专辑封面显示工具，让您的音乐聆听体验更加视觉化。

## 主要特性

- 专辑封面显示（可选4K分辨率）
- 完整的播放控制功能
- 主题切换（深色、主色调、封面背景）
- 实时播放状态更新
- 桌面通知支持
- 响应式设计，自动字体缩放
- 两种显示模式（标准和全屏）
- WebSocket 实时连接
- Docker 容器化部署

## 系统要求

- Docker
- Roon Core 已安装并运行
- 现代网页浏览器

## 快速开始

### 方式一：使用 Docker Compose（推荐）

1. 创建 `docker-compose.yml` 文件：
```yaml
version: '3'
services:
  roonalbumart:
    image: epochaudio/roonalbumart:latest
    container_name: roonalbumart
    ports:
      - "9660:9660"
    restart: unless-stopped
```

2. 运行容器：
```bash
docker-compose up -d
```

### 方式二：直接使用 Docker

```bash
docker run -d \
  --name roonalbumart \
  --network host \
  --restart unless-stopped \
  epochaudio/roonalbumart:latest

```

## 使用方法

1. 启动服务后，打开浏览器访问：`http://<你的IP>:9660`
2. 首次使用时，需要在 Roon Core 中授权此扩展
3. 在界面中选择您要控制的 Roon 区域（Zone）

### 界面说明

- **标准播放界面** (`/nowplaying.html`)
  - 专辑封面和播放信息显示
  - 播放控制（播放/暂停、上一曲/下一曲）
  - 音量控制和播放设置（循环、随机、电台）
  - 可选4K专辑封面显示
  - 支持主题切换
  - 可选桌面通知

- **全屏模式** (`/fullscreen.html`)
  - 基于标准界面的全屏优化版本
  - 最大化显示区域
  - 自动字体缩放

提示：根据使用场景选择合适的显示模式：
- 桌面使用：标准播放界面
- 远距离观看：全屏模式

## 致谢

本项目基于以下开源项目进行开发：

- [Roon Web Controller](https://github.com/pluggemi/roon-web-controller) - 原始项目由 Mike Plugge 开发
- [Roon Web Controller (Miemo Fork)](https://github.com/miemo/roon-web-controller) - 提供了界面优化版本

特别感谢：
- Mike Plugge (@pluggemi) 创建了最初的 Roon Web Controller
- Miemo Penttinen 提供了界面优化版本
- Roon Labs 提供了优秀的音乐播放器和 API
- 所有为这个项目做出贡献的开发者
