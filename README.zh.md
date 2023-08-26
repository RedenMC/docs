[English](README.en.md) | **中文**

<h1 align="center">SphinxTemplate</h1>

<p align="center">
  <b>多语言 Sphinx 文档模板</b>
</p>

<p align="center">
  <a href="LICENSE">
    <img src="https://img.shields.io/badge/License-CC--BY--NC--SA--4.0-important?style=for-the-badge" />
  </a>
</p>

**Sphinx 文档的内容可以使用 Markdown 或 reStructuredText 编写，但索引页面必须使用 *reStructuredText* 编写。**

## 贡献文档指南

**您的提交信息应当遵守 [约定式提交](https://www.conventionalcommits.org/zh-hans/v1.0.0/) 规则**

### 安装文档所需依赖

``` bash
pip3 install -r requirements.txt
```

### 编译文档（将 Sphinx 的 rst/md 文件转换为 html 文件）

（该步骤仅用于预览编辑后的文件）

``` bash
make clean
make html
```

文档会在 `build/html` 目录下以 `en_US`（英语（美国））生成。

如果你需要更改生成的语言，可以将 `source/conf.py` 文件中第 58 行 `language = os.environ.get('READTHEDOCS_LANGUAGE', 'en_US')` 中的 `en_US` 改为你想要的语言。

### 更新翻译文件

（该步骤以中文为例，如果需要使用其他语言，将 `zh_CN` 替换为目标语言）

``` bash
sphinx-build -b gettext ./source ./source/_locale -D language=en_US # 你需要在这里使用文档的原始语言
sphinx-intl update -p ./source/_locale -l zh_CN
```

然后检查 `docs/source/_locale/zh_CN/` 下的 `.po` 文件。更新文件顶部的 `"Last-Translator:` 信息。将其更改为 `YOUR NAME <YOUR EMAIL>`，然后，对于更改：

- 空的翻译字符串会被增加，用于存储新增加的内容的翻译
- `#, fuzzy` 注释会被添加到被更改内容翻译文本处。请更新翻译并移除 `#, fuzzy`
- 被移除的内容的翻译会被移动到 `.po` 文件的末尾并被注释
- 以 `Bases: ` 开头的 `msgid` 字符串不需要被翻译

## 📜 协议&许可证

> **SphinxTemplate 的内容基于 [CC-BY-NC-SA-4.0 许可证](license-translations/LICENSE-zh)（[原文](LICENSE)）发行**

``` text
SphinxTemplate (c) 由 iXORTech, Cubik65536, 以及 所有贡献者 创作.

SphinxTemplate 根据知识共享（Creative Commons）
署名—非商业性使用—相同方式共享 4.0 公共许可协议进行分发。

您应该已经收到了一份许可证的副本。如果没有，
请参见 <http://creativecommons.org/licenses/by-nc/4.0/>。
```

> **SphinxTemplate 的代码使用 [AGPL-3.0-or-later 协议](license-translations/LICENSE-zh.CODE)（[原文](LICENSE.CODE)）作为软件分发许可证**

``` text
SphinxTemplate - 多语言 Sphinx 文档模板
Copyright (C) 2022 iXORTech, Cubik65536 以及 所有贡献者 版权所有。

本程序是自由软件：你可以根据自由软件基金会发布的 GNU Affero 通用公共许可证的条款，
即许可证的第3版或（您选择的）任何后来的版本重新发布它和/或修改它。

本程序的发布是希望它能起到作用。但没有任何保证；甚至没有隐含的保证。本程序的分发
是希望它是有用的，但没有任何保证，甚至没有隐含的适销对路或适合某一特定目的的保证。
参见 GNU Affero 通用公共许可证了解更多细节。

您应该已经收到了一份 GNU Affero 通用公共许可证的副本。如果没有，请参见 <https://www.gnu.org/licenses/>。
```
