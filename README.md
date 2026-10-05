# 视唱旋律生成器（melody-trainer）

一个纯静态的视唱练耳工具：随机生成视唱旋律 → 五线谱展示 → 人声唱名采样播放 / 钢琴伴奏，
支持 iOS 锁屏播放（MediaSession）。从 `singing-trainer`（和弦听辨）项目里独立拆分出来。

**线上地址**：https://3094863155com-ctrl.github.io/melody-trainer/

## 使用

- 选调性 / 旋律长度 / 跳进概率 / 音符密度 → 「生成旋律」
- 「播放」（人声唱名采样，可开关升降号唱法 / 钢琴伴奏 / 各自音量）
- 「渲染播放」= 离线混音成一段音频后播放（iOS 锁屏可控制）
- 循环模式 / 每行小节数 / 音域范围 / 调性均可调

## 本地打开

直接双击 `index.html` 也能看谱面，但**采样必须走 http://**（file:// 下 fetch 被 CORS 拦截，
人声会静音）。推荐：

```bash
python3 -m http.server 8000
# 打开 http://localhost:8000
```

## 目录结构

```
index.html          单页应用（内联全部逻辑）
harmony_melody.js   旋律生成 + 钢琴伴奏（Tone.js 采样器）
vexflow.js          五线谱渲染（VexFlow 1.x，本地打包）
音源/               人声唱名采样（do/re/mi… 两个八度 × 升降号，31 个 mp3）
.nojekyll           让 GitHub Pages 跳过 Jekyll（保住下划线/中文路径）
```

## 依赖

- [Tone.js](https://tonejs.github/) 14.8.49（CDN）
- VexFlow（本地 vexflow.js）

钢琴伴奏用 Tone.js 合成音色，不需要额外采样文件。
