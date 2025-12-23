# christmas-tree-for-tiktok

抖音/短视频风格的“手势控制圣诞树”Demo：Three.js 粒子圣诞树 + MediaPipe 手势识别。
- [英文说明：README_EN.md](README_EN.md)
## 在线体验 / 部署
推荐直接用 **GitHub Pages** 部署（自带 HTTPS，摄像头可用）。
![手势控制](image1.png)
## 本地运行（必看）
请用静态服务器启动（不要直接双击用 `file://` 打开）：

```bash
# Python
python3 -m http.server 8080

# 或 Node
npx serve .
```

打开：`http://localhost:8080/`

### 摄像头权限限制（务必遵守）
浏览器的 `getUserMedia` 只能在“安全上下文”中工作：

- ✅ `https://` 域名
- ✅ `http://localhost` / `http://127.0.0.1`
- ❌ 其它 `http://` 域名（摄像头会被拒绝）

## 操作说明
### 页面按钮
- **📷 添加相片**：上传多张图片，作为树上的“照片粒子”。
- **⚙️ 高级模式**：显示/隐藏左上角调试窗口（含手势骨骼预览、祝福语输入、音乐播放）。
- **🔗 分享好友**：复制当前页面链接。

### 键盘
- `H`：隐藏/显示 UI（标题与底部按钮）。

### 手势（摄像头识别）
- ☝️ 仅食指伸出：随机聚焦放大一张照片（FOCUS）。
- 🖐️ 张开手掌：粒子散开（SCATTER）。
- ✊ 握拳：粒子聚成圣诞树（TREE）。
- 👍 点赞：切换暗色主题（黑色背景）。
- ✌️ 剪刀手：显示金色祝福文字（默认 “Merry Christmas”）。
- 👌 OK：隐藏/显示 UI（同 `H`）。

## 自定义
### 修改祝福语
点击“高级模式”，在输入框修改（最多 20 字符），用于 ✌️ 手势展示。

### 修改背景音乐
在 `index.html` 里修改：

```js
const AUDIO_URLS = [
  "Last-Christmas.mp3" // 示例：你需要自行把该 MP3 放到仓库里，或改成你的文件名/URL
];
```

- 你可以把 MP3 放到仓库中（保持路径可访问）。
- 若不需要音乐：把 `AUDIO_URLS` 设为 `[]`。

## 依赖/资源
本项目为离线版：Three.js、MediaPipe、模型与 WASM 均在 `./libs/` 下，无需 CDN。
