# 新世纪五笔·拼音 Rime 输入方案

这是一个面向 Rime 的新世纪五笔与简体拼音组合输入方案，适用于鼠须管、小狼毫、ibus-rime 等前端。

## 功能

- 使用新世纪五笔输入汉字和词组。
- 在五笔方案中使用反引号 `` ` `` 开启拼音反查。
- 提供独立的袖珍简化字拼音方案。
- 五笔和拼音方案共享 `custom_phrase.dict.yaml` 自定义短语。
- 通过 OpenCC 提供 Emoji 候选。
- 支持使用 Plum（东风破）安装和更新。

## 使用 Plum 安装

本方案的拼音配置依赖 `stroke` 笔画方案。首次安装时执行：

```bash
curl -fsSL https://raw.githubusercontent.com/rime/plum/master/rime-install \
  | bash -s -- stroke FederoZed/Rime
```

如果本地已经安装 Plum，也可以执行：

```bash
bash ~/Library/Rime/plum/rime-install stroke FederoZed/Rime
```

安装完成后，从 Rime 菜单执行“重新部署”。配方会把以下方案加入方案列表：

- 新世纪五笔·拼音
- 袖珍简化字拼音

更新方案时重新执行相同的安装命令，然后重新部署即可。

## 手动安装

将下列文件复制到 Rime 用户目录：

```text
wubixinshiji_pinyin.schema.yaml
wubixinshiji.dict.yaml
pinyin_simp.schema.yaml
pinyin_simp.dict.yaml
custom_phrase.dict.yaml
opencc/emoji.json
opencc/emoji_category.txt
opencc/emoji_word.txt
```

随后将 `wubixinshiji_pinyin` 和 `pinyin_simp` 加入 `default.custom.yaml` 的 `schema_list`，再重新部署。

## 自定义短语

自定义短语保存在 `custom_phrase.dict.yaml`。每条记录包含三列：

```text
短语<Tab>编码<Tab>权重
```

例如：

```text
联系货主未接通<Tab>lhw<Tab>4000
```

其中 `<Tab>` 表示一个真正的 Tab 字符，不能使用空格代替。保存文件并重新部署后，在五笔或拼音方案中输入 `lhw` 即可使用该短语。

## 主要文件

- `wubixinshiji_pinyin.schema.yaml`：新世纪五笔与拼音反查方案。
- `wubixinshiji.dict.yaml`：新世纪五笔主词典。
- `pinyin_simp.schema.yaml`：袖珍简化字拼音方案。
- `pinyin_simp.dict.yaml`：简体拼音词典。
- `custom_phrase.dict.yaml`：两个方案共享的自定义短语。
- `opencc/`：Emoji 转换配置和数据。
- `recipe.yaml`：Plum 安装配方。

## 许可与致谢

本仓库包含不同来源、不同许可状态的文件。详细信息请参阅 `LICENSE` 和 `AUTHORS`。使用或再分发前，请遵守各文件对应的许可及原始权利人的要求。
