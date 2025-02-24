
# RandGen - 随机字符串生成工具

RandGen 是一款灵活的命令行工具，可以根据多种自定义选项生成随机字符串。你可以根据不同的模式生成随机字符串，应用配置并将结果导出到文件。该工具还支持生成输出字符串的哈希值。

## 特性

- 生成随机数字、字母、字母数字组合或 UUID 格式的字符串。
- 配置最小和最大长度。
- 指定生成字符串的数量。
- 使用正则表达式和自定义字符集来生成模式化字符串。
- 将生成的字符串导出到文件并计算其哈希值。
- 支持将配置保存到配置文件（`RandGen.ini`）中。
- 使用强大的表达式语法定义灵活的字符串模式。

## 安装

要使用 RandGen，请克隆代码库或下载脚本文件。

```bash
git clone https://github.com/your-repository/RandGen.git
cd RandGen
```

确保安装了 Python 3.x。

## 使用方法

```bash
RandGen.py [-h] [-l LENGTH | -r] [-c COUNT] [-s] [-S] [-nr] [-i INPUT] [-o OUTPUT] [-hash ALGORITHMS] [-nv] [-set SET] [-add [ADD ...]] [-rm REMOVE] [-up [UP ...]] [-list] -m MODE
```

### 参数说明

- `-m MODE`: 生成模式或表达式。可选值包括：
    - `u`: UUID
    - `n`: 数字
    - `a`: 字母（小写或大写）
    - `an`: 字母数字组合
    - `cc`: 自定义字符集
    - `w`: 写入自定义配置（添加、删除、更新、列出）
    - 表达式：灵活定义字符串生成模式（例如，`[an(10;nr),@test.com]`）。
    - `$`: 引用现有的自定义配置。

- `-l LENGTH`: 生成字符串的长度（指定长度）。
- `-r`: 使用配置中的 `min_length` 和 `max_length` 之间的随机长度。
- `-c COUNT`: 生成字符串的数量。
- `-s`: 强制小写。
- `-S`: 强制大写。
- `-nr`: 不重复字符。
- `-i INPUT`: 自定义字符集（用于 `cc` 模式）。
- `-o OUTPUT`: 将结果导出到文件。
- `-hash ALGORITHMS`: 计算生成字符串的哈希值（例如，`md5,sha256`）。
- `-nv`: 不输出到控制台（禁止输出）。
- `-set SET`: 修改配置文件中的 `min_length` 或 `max_length`。
- `-add [ADD ...]`: 添加新的自定义配置（例如，`re` 或 `cc` 类型）。
- `-rm REMOVE`: 删除自定义配置。
- `-up [UP ...]`: 更新自定义配置。
- `-list`: 列出所有自定义配置。

### 使用示例

1. **生成 5 个 UUID**：
    ```bash
    RandGen -m u --count 5
    ```

2. **生成 10 个随机数字字符串，长度为 6，且数字不重复**：
    ```bash
    RandGen -m n -l 6 --count 10 -nr
    ```

3. **生成长度为 8 的大写字母字符串**：
    ```bash
    RandGen -m a -l 8 -S
    ```

4. **使用表达式生成自定义字符串**：
    ```bash
    RandGen -m "[an(10;nr),@test.com]"
    ```

5. **列出所有自定义配置**：
    ```bash
    RandGen -m w -list
    ```

## 配置文件（`RandGen.ini`）

该工具使用配置文件 (`RandGen.ini`) 来存储设置，例如 `min_length` 和 `max_length`。你可以直接修改这些设置。

完整教程参见：https://www.fcrnext.com/archives/475/01/
