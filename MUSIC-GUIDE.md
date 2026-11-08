# 背景音乐更换说明

## 一、音乐文件放在哪里

把你的音乐文件（推荐 `.mp3` 格式）放到本仓库的 **`music/`** 目录下，和 `index.html` 同级。

目录结构如下：

```
gaobai/
├── index.html          # 网站入口页面
├── music/
│   └── bgm.mp3         # 背景音乐文件（你自己放进来）
├── manyucai.html       # 旧版备份文件（可保留可删除）
└── 音乐更换说明.md
```

- 默认读取的文件名是 `music/bgm.mp3`。
- 文件名和格式可以自己定，但要和下面 `index.html` 里写的 `src` 保持一致。
- 建议用 MP3（兼容性最好）；也可以用 `.wav`、`.ogg`、`.m4a`，但要同步改 `type`。

## 二、在哪里改音乐

打开仓库根目录的 **`index.html`**，找到 `<body>` 开头这段 `<audio>` 标签（约第 23 行）：

```html
<audio id="bgMusic" preload="auto" loop>
    <source src="music/bgm.mp3" type="audio/mpeg">
    您的浏览器不支持音频播放，请升级浏览器
</audio>
```

### 1. 换成仓库内的本地音乐

把 `src` 改成你放进 `music/` 目录的文件路径：

```html
<source src="music/你的歌曲名.mp3" type="audio/mpeg">
```

如果是其他格式，对应修改 `type`：

| 格式 | type 写法 |
|------|-----------|
| MP3  | `audio/mpeg` |
| WAV  | `audio/wav` |
| OGG  | `audio/ogg` |
| M4A  | `audio/mp4` |

### 2. 换成网络链接音乐（外链）

也可以直接把 `src` 写成一个以 `http://` 或 `https://` 开头的音频直链：

```html
<source src="https://example.com/xxx.mp3" type="audio/mpeg">
```

注意：外链必须是音频文件直链（点开能直接播放/下载 mp3），不能是网页地址；临时图床（如 uguu.se）的链接会过期失效，重要歌曲建议放到仓库 `music/` 目录里。

## 三、相关设置说明

- `loop`：加上表示**循环播放**；删掉则只播一遍。
- `preload="auto"`：页面打开时预加载音乐，减少卡顿。
- 浏览器通常禁止页面一打开就自动出声，所以代码里做了兜底：自动播放被拦截时，用户**第一次点击或触摸页面**后音乐才会响起，这是正常现象，不是报错。

## 四、提交后如何生效

1. 把音乐文件拖进 `music/` 目录，改好 `index.html` 里的 `src`。
2. 提交（Commit）到 `main` 分支。
3. 等 GitHub Pages 自动部署（一般 1～2 分钟），访问站点根地址即可：
   https://shi-diqi.github.io/gaobai/

## 五、常见问题

- **没有声音**：先确认 `src` 路径/文件名拼写正确、文件已上传；手机上需先点一下页面才会播放。
- **播放报错**：检查音频格式和 `type` 是否匹配；外链是否可访问、是否允许跨域。
- **想改弹窗文案**：在 `index.html` 的 `<script>` 里找到 `const texts = [...]` 数组，直接修改里面的句子即可。
