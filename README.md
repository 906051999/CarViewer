# CarViewer

本项目旨在实现 PlayCanvas 与 WebUI 的深度集成，打造以"看车面板"为核心功能的交互式应用。

## 项目设计

通过网页提供丰富的 UI 面板（例如按钮、下拉菜单等），用户可以通过这些控件实时控制 PlayCanvas 3D 场景中的各种行为，包括：

*   内外视角切换
*   部件高亮显示
*   动画播放控制
*   车型切换
*   车门开关
*   车漆更换
*   场景切换

本方案完全基于前端技术实现，所有定制参数配置均通过 JSON 文件进行保存，并支持导出和导入功能。

## 技术概览

*   **HTML/CSS/JS (前端框架):** 使用现代前端框架（如 React, Vue 或 Angular）创建用户界面，实现与 PlayCanvas 场景的交互。
*   **PlayCanvas:**  利用 PlayCanvas 引擎渲染 3D 场景，并提供 API 用于控制场景中的对象、动画和效果。
*   **状态管理:** 使用状态管理工具（如 Redux 或 Zustand）来集中管理应用程序的状态，确保 UI 组件和 PlayCanvas 场景之间的数据同步。
*   **事件通信:**
    *   **PlayCanvas -> WebUI:**  PlayCanvas 场景通过事件派发机制（例如 `pc.app.fire()`）向 WebUI 发送事件，通知 UI 更新或触发相应操作。
    *   **WebUI -> PlayCanvas:** WebUI 通过调用 PlayCanvas 提供的 API 或自定义函数来控制场景，例如切换视角、高亮部件等。
*   **数据序列化与反序列化:**  使用 JSON 格式序列化和反序列化数据，用于在 WebUI 和 PlayCanvas 之间传递复杂的数据结构。

## 拓展规划

### 多车型批量适配

**核心思想：配置化驱动，快速生成定制化前端项目**

1.  **标准化资源目录**：建立统一的资源目录结构，存放模型、贴图等资源文件。
2.  **JSON 配置模板**：创建包含所有可配置项的 JSON 模板，例如模型路径、颜色、UI 按钮等。
3.  **自动化构建脚本**：编写脚本，读取 JSON 配置，复制资源文件，修改/生成前端代码，并打包生成可部署项目。
4.  **可视化配置面板**（可选）：
    *   **本地模式**：开发本地可视化界面，方便非技术人员修改 JSON 配置并预览效果。
    *   **云端模式**：
        *   使用后端服务器提供可视化面板服务。
        *   用户在面板中调整配置，实时预览效果。
        *   一键打包生成可部署的车型展示网站。

**流程**：

1.  非技术人员将车型资源放入资源目录。
2.  通过可视化配置面板调整参数。
3.  运行构建脚本（或通过云端面板一键打包），生成新的前端项目。

### 客服模式
1.  **场景同步**: 用户将当前 PlayCanvas 场景配置参数序列化为 JSON，通过客服链接传递给客服。
2.  **场景重建**: 客服端接收 JSON 数据，重建相同的 PlayCanvas 场景。
3.  **P2P 连接**: 客服作为 host，与用户建立 WebRTC Data Channel 连接，实现实时同步和控制。

## 参考

### 竞品

*   **小米 SU7:** [https://gamemcu.com/su7/](https://gamemcu.com/su7/)
    *   Web 服务器: Tengine
    *   JavaScript 图形: Three.js
    *   内容分发网络（CDN）: Alibaba Cloud CDN
*   **汽车之家 VR 看车:** [https://car.autohome.com.cn/vr/list-0-0-0-1.html#](https://car.autohome.com.cn/vr/list-0-0-0-1.html#)
    *   问题跟踪器: Sentry 8.8.0
    *   安全: HSTS
    *   杂项: Open Graph
    *   Web 服务器: Nginx
    *   编程语言: PHP
    *   JavaScript 库: Swiper, jQuery 2.2.4
    *   反向代理: Nginx