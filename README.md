# 中国景点 3D 展示（china-scenic-3d）

基于 **ECharts 中国地图 + Three.js** 的景点 3D 交互展示网页。在地图上点击景点标记，即可进入该景点的 3D 模型浏览界面，支持旋转、平移、缩放与点击拾取。

## 功能

- 中国地图景点标记（涟漪动效 + 悬停简介），目前收录北京、西安、杭州、苏州、成都共 9 个景点
- 3D 场景：鼠标左键旋转 / 右键平移 / 滚轮缩放 / 点击模型拾取详情
- 模型缺失时自动显示占位模型并在信息面板提示，不会页面报错
- 窗口自适应 + 移动端布局适配
- 内存管理：切换景点时自动释放旧模型的几何体与材质

## 运行方式

必须通过本地服务器访问（浏览器 `file://` 协议会拦截模型加载请求）：

```bash
npm run dev
```

然后浏览器打开 http://localhost:7100/

也可以用任意静态服务器，例如 `python -m http.server 7100`。

> 注意：页面依赖 CDN 资源（ECharts、Three.js、阿里云地图 GeoJSON），需要联网。

## 添加 3D 模型

将 GLB 格式模型文件放入 `models/` 目录，文件名与 `index.html` 中 `scenicData` 的 `model` 字段对应：

| 景点 | 文件路径 |
| --- | --- |
| 故宫 | `models/gugong.glb` |
| 长城 | `models/greatwall.glb` |
| 兵马俑 | `models/bingmayong.glb` |
| 大雁塔 | `models/dayanta.glb` |
| 西湖 | `models/xihu.glb` |
| 灵隐寺 | `models/lingyinsi.glb` |
| 拙政园 | `models/zhuozhengyuan.glb` |
| 都江堰 | `models/dujiangyan.glb` |
| 武侯祠 | `models/wuhouci.glb` |

模型文件较大，已在 `.gitignore` 中忽略，不入库。模型来源与许可署名见 [ATTRIBUTION.md](ATTRIBUTION.md)。

## 目录结构

```
china-scenic-3d/
├── index.html      # 页面主体（样式 + 逻辑全部内联）
├── package.json    # 本地开发服务器脚本
├── models/         # 3D 模型目录（GLB 文件放这里）
└── README.md
```
