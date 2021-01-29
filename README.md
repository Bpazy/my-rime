# my-rime

## 安装相关项
| 项 | 安装命令 | 作用 |
| -- | ---- | -------- |
| [袖珍简化字拼音輸入方案](https://github.com/rime/rime-pinyin-simp)  | `rime-install essay-simp` | 使用其中的简化字词库，具有正确的词频 |
| [简化字八股文](https://github.com/rime/rime-essay-simp)  | `rime-install essay-simp` | 词汇表的简化字版本 |
| [双拼输入方案](https://github.com/rime/rime-double-pinyin)  | `rime-install double-pinyin` | 使用其中的小鹤双拼方案 |

## 设置配置文件
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
