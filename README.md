# Mamehinata · YSM 模型包（Java 版）

> Minecraft Java 版 **Yes Steve Model（YSM）** 文件夹格式模型包
> 原作作者：[是Reme](https://space.bilibili.com/3546650257656003)（单人完成）
> 授权：**CC BY 4.0** · 详见 [LICENSE](LICENSE) 与 [ATTRIBUTION.md](ATTRIBUTION.md)

Mamehinata 是一个面向 YSM 模组的玩家模型包，包含主模型、第一人称手臂、动画、贴图、语言文件以及弹射物与载具的替换模型。本仓库以**文件夹格式**开源：模型、动画、贴图的源文件全部可读可改，既能直接丢进游戏加载，也可以用 Blockbench / 文本编辑器二次编辑。

---

## 1. 模型内容

| 项目 | 内容 |
| --- | --- |
| 模型名称 | Mamehinata（游戏内显示名同 `ysm.json` 的 `metadata.name`） |
| 适配 | Yes Steve Model 模组，**建议 2.5.0 及以上**（配置使用了 2.5.0 新增的 `gui_foreground` / `gui_background` 字段） |
| 格式 | 文件夹格式（`ysm.json` 索引，`spec: 2`） |
| 缩放 | `height_scale` / `width_scale` 均为 `0.7` |
| 默认材质 | `textures/default.png` |
| 预览动画 | `gui`（`disable_preview_rotation: true`，选择界面不自转，便于播放 GUI 动画） |
| 轮盘动画 | 基础动作 6 个、坐姿 8 个、舞蹈 14 个 |
| 附加替换 | 箭、浮标（弹射物）；船、矿车（载具） |

### 1.1 外观调节（轮盘「外观」页）

| 控件 | 类型 | 变量 | 范围 |
| --- | --- | --- | --- |
| 高人来了（身高） | 滑条 | `v.g` | -1 ~ 2（步进 0.1） |
| 宽人来了（体宽） | 滑条 | `v.k` | -1 ~ 2（步进 0.1） |
| 平人来了 | 滑条 | `v.p` | -1 ~ 2（步进 0.1） |
| 头部大小 | 滑条 | `v.tbdx` | -0.3 ~ 1（步进 0.1） |
| 鞋子 | 开关 | `v.xzx` | 开 / 关 |
| 帽子 | 开关 | `v.mzx` | 开 / 关 |
| 挎包 | 开关 | `v.kbx` | 开 / 关 |
| 耷拉耳朵 | 开关 | `v.ed` | 开 / 关 |

### 1.2 表情（轮盘「表情」页）

| 控件 | 档位 |
| --- | --- |
| 眼睛 `v.yjx` | 默认 / 生气 / 哭哭 / `>   <` / `O   O` / 闭眼（共 6 档） |
| 嘴 `v.zmr` | 默认 / 微张 / 倒V嘴 / 猫猫嘴 / 一字嘴 / V字嘴 / X字嘴 / 歪嘴 / 张开（共 9 档） |
| 脸色 `v.lsx` | 默认 / 脸红 / 脸黑（共 3 档） |

### 1.3 动作列表

- **基础动作**：鼓掌、打招呼、行、否、耶好、御笔摇
- **坐姿**：坐下 1–6、随地大小睡、坐在边缘
- **舞蹈**：萝莉摇、鹿乃子虎视眈眈、催眠术、星辉闪耀、橙色正义、互联网过度依存、摇啊摇、摇摇乐、开车车、致命公司摇、快远离互联网、alice didida、谎言舞者、低皮质醇

---

## 2. 目录结构

```
.
├── ysm.json                      # 资源描述文件（固定名称，必须在根目录）
├── models/                       # 模型 JSON
│   ├── main.json                 #   玩家主模型（约 303 KB）
│   ├── arm.json                  #   第一人称手臂
│   ├── arrow.json                #   箭（替换弹射物）
│   ├── fishing_bobber.json       #   浮标（替换弹射物）
│   ├── boat.json                 #   船（替换载具）
│   └── minecart.json             #   矿车（替换载具）
├── animations/                   # 动画 JSON（基岩版 1.8.0 格式）
│   ├── main.animation.json       #   主模型动画（约 192 KB）
│   ├── extra.animation.json      #   轮盘动画（约 1.25 MB）
│   ├── arrow.animation.json
│   ├── boat.animation.json
│   └── unknown.animation.json
├── textures/                     # 贴图
│   ├── default.png               #   默认材质
│   ├── arrow.png / boat.png / fishing_bobber.png / minecart.png
│   └── gui/                      #   模型选择界面背景与前景（background.png / foreground.png）
├── avatar/author-avatar.jpg      # 作者头像（模型详情页展示）
├── lang/zh_cn.json、en_us.json    # 模型内文案的中文 / 英文翻译
├── controller/                   # 动画控制器（预留，当前为空）
├── functions/                    # 自定义函数（预留，当前为空）
└── sounds/                       # 音效（限定 ogg，预留，当前为空）
```

> 说明：YSM 除 `ysm.json` 外不限制文件名与子目录层级，因此本仓库的路径可以自由调整，只要同步修改 `ysm.json` 中的引用即可。

---

## 3. 安装与使用

1. 在客户端（以及需要同步的服务端）安装 **Yes Steve Model** 模组，版本建议 2.5.0+，并确认与你的游戏版本、加载器（Forge / NeoForge / Fabric）匹配。
2. 将本仓库**整个文件夹**放到：

   ```
   .minecraft/config/yes_steve_model/custom/
   ```

   文件夹名即游戏内的模型 ID，可自行改名（例如改成 `Mamehinata`）。
3. 进入游戏后按 `Alt` + `Y`（Forge / NeoForge）或 `Y`（Fabric）打开模型选择界面；也可点击界面右上角「打开模型文件夹」按钮核对模型放置位置。
4. 三种加载形式均可用：**文件夹**、**zip 压缩包**、**.ysm 加密包**。本仓库给的是文件夹形式，便于修改。

注意事项：

- 放在 `custom/` 下**无需授权**即可使用；放在 `auth/` 下则需要授权。本模型 `ysm.json` 中 `"free": false`，即允许被设置为授权模型。
- `.ysm` 是加密格式，导出后**无法再还原为可编辑的源文件**，也仅向上不兼容（高版本导出的包在低版本加载不了）。若要保留可编辑性，请一直使用文件夹或 zip 形式分发。
- 修改 `ysm.json` 时请保持 **UTF-8 无 BOM** 编码，否则模组可能读取失败。

---

## 4. 二次编辑建议

- **模型**：`models/main.json` 为基岩版 1.12.0+ 几何格式，可直接用 Blockbench 的「Bedrock Model」导入编辑；贴图在 `textures/default.png`，改完保持同名或用 `ysm.json` 的 `texture` 数组追加新材质。
- **动画**：`animations/*.animation.json` 为基岩版 1.8.0 格式，Blockbench 可直接打开。
- **轮盘与表情**：新增动画需同时改 `ysm.json` 的 `properties.extra_animation`（或在 `extra_animation_classify` 中归入分类）；`#分类` 前缀表示子菜单，`#按钮` 前缀表示配置面板。
- **提交前自检**（Python 3）：

  ```bash
  python -c "import json;json.load(open('ysm.json',encoding='utf-8'));print('ysm.json OK')"
  ```

  再确认 `ysm.json` 里引用的每个路径都真实存在，且大小写完全一致（Linux 服务端区分大小写）。

---

## 5. 作者与授权

- **原作作者**：是Reme（Bilibili UID `3546650257656003`），模型、动画、贴图均为其原创作品。
- **授权方式**：原作品声明为 **CC BY**（Creative Commons Attribution），本仓库据此以 **CC BY 4.0** 开源发布，并已获得原作者许可。
- **本仓库的改动**：仅做仓储整理（清理 macOS `.DS_Store`、将作者头像 `微信图片_20260804192555_14_12.jpg` 重命名为 `avatar/author-avatar.jpg` 并同步 `ysm.json` 引用、补充文档与 git 配置），**未修改任何模型 / 动画 / 贴图内容**。
- **再分发要求**（CC BY 4.0）：署名原作者「是Reme」与本仓库链接、附许可证链接、注明是否修改。完整署名样例见 [ATTRIBUTION.md](ATTRIBUTION.md)。
- **相关链接**：YSM 模组 [Modrinth](https://modrinth.com/mod/yes-steve-model) · 作者爱发电 [afdian.com/a/ysmmod](https://afdian.com/a/ysmmod)

---

## 6. 免责声明

本仓库不包含 Minecraft 原版游戏素材；Yes Steve Model 模组的代码与内置模型版权归其各自作者所有。模型包按 CC BY 4.0「按现状」提供，使用与修改风险自负。

---

## English Summary

**Mamehinata** is an open-source player model pack for **Yes Steve Model (YSM)** on Minecraft Java Edition, released in folder format so every model, animation and texture stays editable.

- **Original author**: 是Reme (Bilibili UID `3546650257656003`), declared **CC BY**; this repository is published under **CC BY 4.0** with the author's permission.
- **Compatible with**: YSM 2.5.0+ (config uses the 2.5.0 `gui_foreground` / `gui_background` fields).
- **Install**: copy the whole folder into `.minecraft/config/yes_steve_model/custom/`; the folder name becomes the in-game model ID.
- **Features**: height / width / head-size sliders, shoe / hat / bag / droopy-ears toggles, 6 eye states, 9 mouth states, 3 face-colour states, 6 gestures, 8 sitting poses, 14 dances, plus arrow / fishing-bobber and boat / minecart model replacements.
- **Editing**: `models/*.json` (Bedrock 1.12.0 geometry) and `animations/*.json` (Bedrock 1.8.0) open directly in Blockbench. Keep `ysm.json` in UTF-8 without BOM and update its paths whenever you rename files.
- **License**: CC BY 4.0 — attribution required, indicate changes. See [LICENSE](LICENSE) and [ATTRIBUTION.md](ATTRIBUTION.md).
