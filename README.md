[English](#english) | [简体中文](#%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87)

<br>

# English

This is an online implementation of the configuration file preprocessing (parser) and mixin tool, based on the features of Clash For Windows (CFW).

Even if CFW is no longer updated, you can continue to use their parser and mixin features online without being limited to any specific implementation.

## Disclaimer

This tool is only used for modifying YAML configuration files and is merely a plain text file editing tool. It does not contain any content that violates the laws and regulations of any country.

## warn

It is not recommended to use this service built by others. Your query parameters are likely to be recorded, thus revealing your subscription.

Although it doesn't happen by default, it only takes 2 lines of code to change.

## Features

- Supports preprocessing of YAML configuration files.
- Implements basic parser and mixin features. (For functionality, please refer to the CFW documentation)
- Advanced features may not be fully implemented; please refer to the examples in this project.

## Typical Use Cases

1. Convert from a subscription to get a subscription link, specifying your favorite rule set.
2. The rule set lacks certain rules or some rules are inappropriate.
3. Use the parser feature to add elements like nodes, rules, node groups, etc., to the configuration file.
4. Use the mixin feature to override parts of the configuration file, such as overriding enhanced-mode: fake-ip.
5. Obtain a satisfactory configuration file subscription link.

——————

1. Multiple device usage, frequently changing subscriptions.
2. Use the magic number feature, all devices use the same link.
3. The initial design intention was to require a parser, so you need to place a valid parser.yaml.
4. When updating subscriptions, only update the subscription link in the source.txt on the server.
5. All devices can update their subscriptions accordingly.

## Processing Workflow

1. Obtain the subscription link from local or query parameters (Clash format).
2. Obtain parser.yaml from local or query parameters.
3. Obtain mixin.yaml from local or query parameters.
4. Download the subscription from the link and use mixin.yaml to override its content.
5. Use parser.yaml to preprocess it.
6. Return the configuration file in Clash format.

## Usage Instructions

### Quick Deployment

Deploy directly on the server and start with:

`
python3 parser.py
`


Then use NGINX or similar reverse proxy for SSL and port modification.

You can also easily deploy this application on serverless platforms like Vercel.

After deployment, send requests by constructing the following URL:

```
https://your.domain/?source=<base64-encoded-subscription-url>&parser=<base64-encoded-parser.yaml-url>&mixin=<base64-encoded-mixin.yaml-url>
```

### Parameter Explanation

- `source`: Base64 encoded subscription link (Clash format)
- `parser`: Base64 encoded `parser.yaml` download link, with the same format as CFW's parser, content as per the example files in this project.
- `mixin`: Base64 encoded `mixin.yaml` download link, with the same format as CFW's mixin, this parameter is optional, content as per the example files in this project.

For example:

```
https://example.com/?source=aHR0cDovL2xvY2FsaG9zdDoyNTUwMC9zdWI/dGFyZ2V0PWNsYXNoJm5ld19uYW1lPXRydWUmdXJsPXRlc3QmaW5zZXJ0PWZhbHNlJmNvbmZpZz1odHRwcyUzQSUyRiUyRnJhdy5naXRodWJ1c2VyY29udGVudC5jb20lMkZBQ0w0U1NSJTJGQUNMNFNTUiUyRm1hc3RlciUyRkNsYXNoJTJGY29uZmlnJTJGQUNMNFNTUl9PbmxpbmUuaW5p&parser=aHR0cHM6Ly9leGFtcGxlLmNvbS9wYXJzZXIueWFtbA==&mixin=aHR0cHM6Ly9leGFtcGxlLmNvbS9taXhpbi55YW1s
```


### personal use

For personal use, if you are too lazy to pass parameters, you can use a preset magic number (defaults to 'jynb') to automatically read the configuration from a local file:

- Create `source.txt` and `mixin.yaml` in the same directory or the upper directory of `parser.py`.
- The first line of `source.txt` should write the subscription link, and the second line should write the encoding type of the subscription link (raw, url_encode or base64).

For example:

```
https://example.com/?source=jynb&mixin=jynb
```



<br>
<br>
<br>
<br>
<br>





# 简体中文

这是一个在线实现的配置文件预处理 (parser) 和 mixin 工具，基于 Clash For Windows（CFW）的功能。

即使 CFW 不再更新，你也可以通过这个工具在线继续使用它们的 parser 和 mixin 功能，且不再受限于某某实现。

为众人拾柴者，还是冻毙于风雪了。

## 免责声明

此工具仅用于对 YAML 配置文件进行修改，只是一个纯文本文件修改工具。它不包含违反任何国家法律法规的内容。

## 警告

不建议使用别人搭建的此服务，你的查询参数很可能会被记录，从而泄露你的订阅。

虽然默认不会，但要改也就 2 行代码的事。

## 功能特性

- 支持 YAML 配置文件的预处理。
- 实现基本的 parser 和 mixin 功能。（功能请参考 CFW 文档）
- 高级功能可能实现不全，请参考项目中的示例。

## 典型使用场景

1. 从订阅转换获取订阅链接，并指定自己喜欢的规则集
2. 该规则集少了某些规则或者某些规则不合适
3. 使用 parser 功能向配置文件添加如节点、规则、节点组等
4. 使用 mixin 功能覆盖配置文件中的部分内容，如覆盖 enhanced-mode: fake-ip
5. 获得自己满意的配置文件订阅链接

——————

1. 多设备使用，经常更换订阅
2. 使用幻数功能，各设备都使用同一个链接
3. 设计初衷就是要 parser 的，所以你需要放置一个有效的 parser.yaml
4. 更新订阅时只需要更新服务器上 source.txt 中的订阅链接
5. 各设备更新订阅即可

## 处理流程

1. 从本地或查询参数获取订阅链接（clash 格式）
2. 从本地或查询参数获取 parser.yaml
3. 从本地或查询参数获取 mixin.yaml
4. 从订阅链接下载订阅并使用 mixin.yaml 对其内容进行覆盖
5. 使用 parser.yaml 对其进行预处理
6. 返回 clash 格式配置文件

## 使用说明

### 快速部署

部署在服务器上直接启动即可

```
python3 parser.py
```

然后使用 NGINX 等反向代理进行 SSL，修改端口等。



你也可以轻松地在如 Vercel 这样的无服务器平台上部署此应用。

部署后，通过构造以下 URL 发送请求：

```
https://your.domain/?source=<base64-encoded-subscription-url>&parser=<base64-encoded-parser.yaml-url>&mixin=<base64-encoded-mixin.yaml-url>
```

### 参数说明

- `source`: base64 编码后的订阅链接（Clash 格式）
- `parser`: base64 编码后的 `parser.yaml` 下载链接，格式与 CFW 的 parser 相同，内容可参考本项目示例文件
- `mixin`: base64 编码后的 `mixin.yaml` 下载链接，格式与 CFW 的 mixin 相同，此参数是可选的，内容可参考本项目示例文件

例如：

```
https://example.com/?source=aHR0cDovL2xvY2FsaG9zdDoyNTUwMC9zdWI/dGFyZ2V0PWNsYXNoJm5ld19uYW1lPXRydWUmdXJsPXRlc3QmaW5zZXJ0PWZhbHNlJmNvbmZpZz1odHRwcyUzQSUyRiUyRnJhdy5naXRodWJ1c2VyY29udGVudC5jb20lMkZBQ0w0U1NSJTJGQUNMNFNTUiUyRm1hc3RlciUyRkNsYXNoJTJGY29uZmlnJTJGQUNMNFNTUl9PbmxpbmUuaW5p&parser=aHR0cHM6Ly9leGFtcGxlLmNvbS9wYXJzZXIueWFtbA==&mixin=aHR0cHM6Ly9leGFtcGxlLmNvbS9taXhpbi55YW1s
```

### 个人使用

对于个人使用，如果懒得传递参数，可以使用预设的幻数（默认为 'jynb'）从本地文件自动读取配置：

- 在 `parser.py` 的同目录或上层目录创建 `source.txt` 和 `mixin.yaml`。
- `source.txt` 的第一行应写入订阅链接，第二行写订阅链接的编码类型（raw、url_encode 或 base64）。

例如：

```
https://example.com/?source=jynb&mixin=jynb
```


