# lsearch

**像 Google 一样，搜你本地的文档。**

lsearch 为你电脑里的文档、源码、PDF 和电子书建立全文索引。输入几个关键词，立刻定位到是哪个文件、哪一行、哪一句。全程离线，索引和内容都存在你自己的硬盘上。

官网：https://www.sanbucun.cc/lsearch.html

> 本仓库仅用于发布安装包。源码不在此处。

---

## 下载

前往 [**Releases**](https://github.com/cmzhaopeng/lsearch-releases/releases/latest) 页面下载。

| 平台 | 架构 | 文件 |
|---|---|---|
| Windows 10 / 11 | x64 / ARM64 | `lsearch-*-installer.exe` |
| macOS 11+ | Intel + Apple Silicon 通用 | `lsearch-*-universal.dmg` |
| Ubuntu / Debian / 麒麟 | x64 / ARM64 | `lsearch_*.deb` |
| Fedora / RHEL / openEuler | x64 / ARM64 | `lsearch-*.rpm` |

每个版本均附 `SHA256SUMS`，建议下载后校验。

### Linux 用户请按发行版选择构建版本

Linux 包分两种构建，区别在于链接的 WebKit 版本：

| 构建 | 适用发行版 |
|---|---|
| `webkit40` | 麒麟 V10、Ubuntu 20.04–22.04、Debian 11–12、RHEL 8+、openEuler |
| `webkit41` | Fedora 40+、Ubuntu 24.04+、Debian 13+ |

不确定就先试 `webkit41`，装不上再换 `webkit40`。

包名里带有构建标识，例如 `lsearch_1.0.0-1+webkit41_amd64.deb`、`lsearch-1.0.0-1.webkit41.x86_64.rpm`。

### 安装

```bash
# Debian / Ubuntu / 麒麟
sudo apt install ./lsearch_*_amd64.deb
```

```bash
# Fedora / RHEL / openEuler
sudo dnf install ./lsearch-*.x86_64.rpm
```

Windows 双击安装包；macOS 打开 dmg 后拖入「应用程序」。

### 校验下载

```bash
sha256sum -c SHA256SUMS --ignore-missing
```

---

## 功能一览

- **搜正文，不只是文件名** —— Office 文档、PDF、电子书、源码、纯文本，内容全部进索引
- **27 种格式** —— Word / Excel / PowerPoint（含 doc/xls/ppt 老格式）、WPS 的 wps/et/dps、LibreOffice ODF、RTF、PDF、HTML、纯文本与各类源码，以及 EPUB / MOBI / AZW / AZW3 / FB2 电子书
- **中文搜得准** —— 专为中文做的分词方案，两个字的中文词也能精确命中
- **Google 式查询语法** —— 多关键词 AND、`OR` 分组、`-` 排除、`"精确短语"`，以及 `path:` / `name:` 通配符过滤
- **正则搜索** —— 内置 RE2 正则全文扫描，可选用 AI 根据自然语言描述生成正则
- **内置编辑器** —— 结果直接在侧边栏打开并跳到命中位置，语法高亮，改完即存
- **增量索引** —— 只处理变动过的文件，可开启实时监听
- **四种界面语言** —— 简体中文 / 繁體中文 / English / 日本語，默认跟随系统

## 隐私

lsearch 没有云端、没有账号、没有遥测。索引和提取出的正文全部存放在你本机的数据目录里。程序不常驻后台服务，也不开监听端口。

唯一可选的联网功能是「AI 生成正则」：它只把你输入的描述和你主动粘贴的示例文本，发送给你自己配置的模型接口。文件内容、索引与搜索历史都不参与。不配置 API Key，该功能不存在。

默认路径：

- 配置 `~/.config/lsearch/config.json`
- 数据 `~/.local/share/lsearch/`（可在「设置 → 存储位置」中迁移）

## 系统要求

- **Windows** 10 / 11
- **macOS** 11 或更高
- **Linux** 需 WebKit2GTK（见上方构建选择），部分文档格式需要 LibreOffice；PDF 建议安装 `poppler-utils` 以获得更好的文本提取效果

## 反馈

使用中遇到问题，欢迎在 [Issues](https://github.com/cmzhaopeng/lsearch-releases/issues) 反馈，或发邮件到 zhaopeng@sanbucun.cc。

## 许可

本软件为专有软件，免费提供给个人与企业使用。详见 [LICENSE](LICENSE)（最终用户许可协议）与 [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md)（第三方开源组件声明）。
