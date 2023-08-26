**English** | [中文](README.zh.md)

<h1 align="center">SphinxTemplate</h1>

<p align="center"> 
  <b>Template for multi-lang Sphinx documentation</b>
</p>

<p align="center">
  <a href="LICENSE">
    <img src="https://img.shields.io/badge/License-CC--BY--NC--SA--4.0-important?style=for-the-badge" />
  </a>
</p>

**The content of the Sphinx document can be written in Markdown or reStructuredText, except for the index page, which MUST be written in *reStructuredText*.**

## Guide to contribute to the documentation

**Your commit messages should follow the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) guidelines**.

### Install the requirements

``` bash
pip3 install -r requirements.txt
```

### Build the documentation (convert Sphinx rst/md to html)

(This step is only for preview the edited files)

``` bash
make clean
make html
```

The documentation will be generated in `build/html` directory in `en_US (English (US)).

If you need to change the language of the generated documentation, you can modify the `en_US` of `language = os.environ.get('READTHEDOCS_LANGUAGE', 'en_US')` of line 58 of `source/conf.py` file to your designated language.

### Update the translation files

(This step uses Simplified Chinese as an example, if you need to use other languages, replace `zh_CN` with your designated language)

``` bash
sphinx-build -b gettext ./source ./source/_locale -D language=en_US # You need to use the original language of the documentation here
sphinx-intl update -p ./source/_locale -l zh_CN
```

Then check che changed `.po` files in `docs/source/_locale/zh_CN/`. Update the `"Last-Translator:` information at the top of the file. Change it to `YOUR NAME <YOUR EMAIL>`, and then, for the changes:

- Empty translations will be generated for new texts
- `#, fuzzy` comments will be added to the translation for changed texts. Fix the translation and remove the `#, fuzzy` comment
- Translations for removed texts will be moved to the bottom of the `.po` file and be commented out
- Those msgid starts with `Bases: ` for base class displaying in auto-gen classes don't need to be translated

## Auto build server

```bash
sphinx-autobuild ./source ./build/html
```

Add `-D language=zh_CN` to the end if you want to autobuild a Chinese version of the doc

## 📜 License

> **Contents of SphinxTemplate are licensed under [CC-BY-NC-SA-4.0 License](LICENSE).**

``` text
SphinxTemplate (c) by iXORTech, Cubik65536, and contributors.

SphinxTemplate is licensed under a
Creative Commons Attribution-NonCommercial 4.0 International License.

You should have received a copy of the license along with this
work. If not, see <http://creativecommons.org/licenses/by-nc/4.0/>.
```

> **Codes of SphinxTemplate uses [AGPL-3.0-or-later License](LICENSE.CODE) as software license.**

``` text
SphinxTemplate - Template for multi-lang Sphinx documentation
Copyright (C) 2022 iXORTech, Cubik65536, and contributors.

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```
