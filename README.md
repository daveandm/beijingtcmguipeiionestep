# 规培助手 V1.2.0（by dave）

> 为中医住院医师规范化培训做的桌面辅助工具 —— 把「抄病历、对轮转、赶进度」这些重复劳动自动化，把时间留给临床。

支持 **北京中医药大学东直门医院** 与 **北京中医药大学第三附属医院** 两套 HIS 版式。
**所有病例数据只保存在你自己电脑上**，不上传任何服务器；程序本身不需要注册、不需要登录。

---

## 下载

👉 **安装包在 [Releases 页面](https://github.com/daveandm/beijingtcmguipeiionestep/releases/latest)**，点下面的链接可直接下载：

| 版本 | 大小 | 适用情况 |
|---|---|---|
| [**标准版**（推荐大多数同学）](https://github.com/daveandm/beijingtcmguipeiionestep/releases/download/v1.2.0/GuipeiAssistant-V1.2.0-Setup-Standard.exe) | 330 MB | 没有独立显卡，或不确定自己显卡型号 —— 纯 CPU，任何电脑都能装 |
| [**含 v6 GPU 版**](https://github.com/daveandm/beijingtcmguipeiionestep/releases/download/v1.2.0/GuipeiAssistant-V1.2.0-Setup-with-v6-GPU.exe) | 1.9 GB | 有 **NVIDIA 独立显卡**，识别更准；安装时自动检测显卡，没有 N 卡会自动只装标准部分 |

配套文档（建议先看）：

| 文件 | 说明 |
|---|---|
| [安装说明 Install-Guide.txt](https://github.com/daveandm/beijingtcmguipeiionestep/releases/download/v1.2.0/Install-Guide.txt) | 装之前必读：环境要求、安装步骤、卸载、v6 显卡判断 |
| [使用说明 User-Manual.txt](https://github.com/daveandm/beijingtcmguipeiionestep/releases/download/v1.2.0/User-Manual.txt) | 各功能模块怎么用、数据存在哪、常见问题排查 |
| [使用教程 Quick-Start-Tutorial.docx](https://github.com/daveandm/beijingtcmguipeiionestep/releases/download/v1.2.0/Quick-Start-Tutorial.docx) | 图文教程，第一次用建议通读一遍 |

> **为什么附件是英文名？** 中文文件名在部分系统/浏览器下载时会乱码，所以附件用英文命名。
> 程序界面、安装界面和文档内容**全部是中文**，不影响使用。
>
> **安装路径请保持默认**（`C:\Users\<用户名>\AppData\Local\GuipeiAssistant`），不要装到含中文的路径，否则 OCR 会失效。
> 安装全程**不需要管理员权限**。若 360 / 火绒等杀毒软件拦截，请选「允许」。

---

## 它解决什么问题

规培期间要反复做三件很费时间的事：把住院/门诊病人信息抄进系统、盯着各科室还差多少病例、把一堆记录逐条提交到网站。这个工具把这套流程做成了「拍照片 → 自动识别 → 核对 → 一键批量提交」。

---

## 功能

### 智能识别（三种通道，可切换）
- 住院列表 / 门诊列表 / 门诊病历单的截图或照片 → 结构化数据
- **本地 PP-OCRv4**（CPU，默认，完全离线，开箱即用）
- **本地 PP-OCRv6**（GPU 加速，识别质量更高，需 NVIDIA 显卡）
- **云端视觉大模型**（任意 OpenAI 兼容接口，如 DeepSeek；识别效果与 v6 接近）

### 数据提取与纠错
- **ICD-10 医保码表自动纠名**：支持 `(I63.902)` 单码，也支持 `(I51.201+G32.8)` 组合码
- **中医诊断辅助**：内置《中医病证分类与代码》码全表与中西医对应库，西医诊断可自动对应「中医病名 / 证型」
- **科室名自动对齐轮转表**：容忍别名、分区写法、OCR 残缺字形
- **日期自动规范**为 `yyyy-mm-dd`（两位年补全、去掉时间部分）

### 进度看板
- 按轮转表自动统计各科室缺口，卡片化展示「已做 / 要求」
- 勾选科室 → 「提交选中科室」一键批量提交（按组级科室匹配，防漏交）
- 临床技术缺口可自动补足

### 自动化提交（Playwright + Edge）
- 自动登录（登录态本地保存，只需第一次手动登录）
- 科室自动匹配、批量提交
- **非法日期拦截** + **提交后回读校验**，防止「假成功」
- **提交账号双重校验**，防止把记录交到别人账号下

### 门诊病历录入
- 东直门「文书式」与三附院「标签式」两种版式自动识别
- 卡片式预览，可拖动连续勾选、可编辑、支持备注整篇提交
- 表格支持直接双击编辑，有撤销（↶）功能，可 Ctrl+S 存回库

---

## 运行环境

| 项目 | 要求 |
|---|---|
| 系统 | Windows 10 / 11（64 位） |
| 浏览器 | 系统自带 **Microsoft Edge**（登录和提交网站时使用，请勿卸载） |
| 离线使用 | 标准功能与本地识别**完全离线可用** |
| 需要联网 | 仅「提交到网站」时 |
| v6 GPU 版额外要求 | NVIDIA 显卡 + 显存 2 GB 以上 + 较新的显卡驱动 |

> AMD 显卡、Intel 核显**不能**用 v6（装了也跑不起来），请选标准版。
> 判断方法：桌面右键「显示设置 → 高级显示」看适配器名称，或 `Win+R` 输入 `dxdiag` 在「显示」标签页查看。

---

## 你的数据在哪

```
C:\Users\<你的用户名>\AppData\Local\规培助手\
  ├─ config.json          你的配置
  ├─ data\users\<姓名>\   病例库（住院病种 / 门诊病种 / 临床技术 / 门诊病历）
  ├─ .edge-profile\       网站登录状态
  └─ crash.log            异常日志（出问题时看这个）
```

- 换电脑：把整个「规培助手」文件夹拷到新电脑同一位置即可。
- 卸载时会询问是否删除个人数据：选「否」则保留，重装可继续用（推荐）。
- **数据不会离开这台电脑**，除非你自己在设置里填入云端大模型的 API Key 走云端识别通道。

---

## 常见问题

<details>
<summary><b>识别点了没反应 / 提示「v6 通道不可用」</b></summary>

说明 v6 环境有问题，程序已自动回退到本地 v4，功能不受影响，只是精度略低。
想彻底查清：双击安装目录下的「v6诊断工具.bat」，它会生成一份《诊断报告.txt》。
</details>

<details>
<summary><b>程序打不开 / 一闪而过</b></summary>

运行安装目录下的「排错启动（看报错）.bat」，它会带控制台启动，能直接看到报错文字。
崩溃详情也记在 `%LOCALAPPDATA%\规培助手\crash.log`。
</details>

<details>
<summary><b>看板是空的 / 自动生成临床技术没反应</b></summary>

先到「设置」确认三张表格路径都能打开，再点页面上的「查看库」刷新。
</details>

<details>
<summary><b>看板提示「未在轮转表中找到该用户」</b></summary>

轮转表里没有你的姓名，或写法不一致（多空格、简繁差异）。到「设置 → 表格与提交」换成正确的轮转表，或核对姓名写法。
</details>

<details>
<summary><b>提示找不到 Edge / Excel 保存失败</b></summary>

- 找不到 Edge：用 Windows 更新或官网装一下 Microsoft Edge。
- Excel 保存失败：该表格正在 Excel 里打开着，先关掉 Excel 再操作。
</details>

---

## 版本

**V1.2.0** — 源码特性与上一版一致（v4 本地 OCR + v6 GPU 通道 + 云端通道），
对 `ocr_engine.py` / `align.py` / `gui.py` / `extractor.py` 做了功能调整，接口未变。

---

## 说明

本项目为个人在规培期间自用的辅助工具，按实际使用需要持续调整。
使用中遇到问题、或想要某个功能，欢迎到 [Issues](https://github.com/daveandm/beijingtcmguipeiionestep/issues) 反馈，附上《诊断报告.txt》或 `crash.log` 能更快定位。

> 本工具仅用于辅助整理个人规培记录，**录入内容请务必逐条核对后再提交**；
> 医疗数据请遵守所在医院的保密与信息安全规定。
