# my-rime

## 安装相关项
| 项 | 安装命令 | 作用 |
| -- | ---- | -------- |
| [袖珍简化字拼音輸入方案](https://github.com/rime/rime-pinyin-simp)  | `rime-install essay-simp` | 使用其中的简化字词库，具有正确的词频 |
| [简化字八股文](https://github.com/rime/rime-essay-simp)  | `rime-install essay-simp` | 词汇表的简化字版本 |
| [双拼输入方案](https://github.com/rime/rime-double-pinyin)  | `rime-install double-pinyin` | 使用其中的小鹤双拼方案 |

## 设置配置文件
### 1. 添加简体中文词库
在 Rime 的“用户文件夹”下新建 `extended.dict.yaml`: 
```yaml
# Rime dictionary
# encoding: utf-8

---
name: extended
version: "2020.12.30"
sort: by_weight
vocabulary: essay-zh-hans
use_preset_vocabulary: true

import_tables:
  - pinyin_simp
...
```

### 2. 设置双拼方案
在 Rime 的“用户文件夹”下新建 `double_pinyin_flypy.custom.yaml`:
```yaml
patch:
  translator/dictionary: extended
  translator/preedit_format: []
  switches:
    - name: ascii_mode
      reset: 1 # 1为默认英文，0为默认中文
  vocabulary: essay-zh-hans
  punctuator:
    # 我不会使用全角英文的，我觉得其他程序员也不会。
    # 但是中文的标点又是全角的，所以我就只留下半角然后改它的标点。
    half_shape:
      "!": "！"
      '"':
        pair:
          - "“"
          - "”"
      "#": "#"
      "$": "￥"
      "%": "%"
      "&": "&"
      "'":
        pair:
          - "‘"
          - "’"
      "*": "*"
      "+": "+"
      ",": "，"
      "-": "-"
      ".": "。"
      "/": "/"
      "\\": "、"
      ":": "："
      ";": "；"
      "=": "="
      "?": "？"
      "@": "@"
      "(": "（"
      ")": "）"
      "[": "【"
      "]": "】"
      "{": "「"
      "}": "」"
      "<": "《"
      ">": "》"
      "^": "……"
      "_": "——"
      "`": "`"
      "|": "|"
      "~": "~"
```

### 3. 设置 Rime 默认行为
在 Rime 的“用户文件夹”下存在 `default.custom.yaml` 文件，编辑并添加下面内容:
```yaml
patch:
  "ascii_composer/switch_key":
    Shift_L: commit_code
    Shift_R: commit_code
  schema_list:
    - {schema: double_pinyin_flypy}
```

### 4. 设置 weasel 样式
在 Rime 的“用户文件夹”下存在 `weasel.custom.yaml` 文件，编辑并添加下面内容:
```yaml
patch:
  "style/font_face": "微软雅黑"
  "style/color_scheme": aqua
  "style/horizontal": true
  app_options/cmd.exe:
    ascii_mode: false
  app_options/conhost.exe:
    ascii_mode: false
```
