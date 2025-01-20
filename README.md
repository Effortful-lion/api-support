# API 文件语法高亮扩展
此扩展仅用于自己学习使用

## 功能

此扩展为 `.api` 文件提供语法高亮支持，特别是针对以下内容：
- `service` 关键字
- `@handler` 注解及其后内容
- HTTP 请求方法（`get`、`post`、`put`、`delete`）
- `returns` 关键字
- Go 语言中的注释、类型、变量等

## 安装步骤

1. 确保你已经安装了 [Visual Studio Code](https://code.visualstudio.com/)。
2. 下载并安装此扩展：
   - 从 [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/vscode) 搜索并安装此扩展。
   - 或者下载 `.vsix` 文件并在 VS Code 中手动安装。

## 使用方法

1. 安装扩展后，打开一个包含 `.api` 文件的项目。
2. 打开 `.api` 文件，你将看到语法高亮效果。
3. 语法高亮规则包括：
   - `service` 关键字使用与 `type` 关键字相同的颜色。
   - `@handler` 注解及其后内容使用绿色。
   - HTTP 请求方法（`get`、`post`、`put`、`delete`）使用红色。
   - `returns` 关键字使用红色。
   - Go 语言中的注释、类型、变量等使用相应的颜色。

## 示例

以下是一个示例 `.api` 文件：

```go
// 以 用户管理 的两个重要接口为例，演示如何使用写 api 文件
type LoginRequest {
    Username string `json:"username"`
    Password string `json:"password"`
}

type LoginResponse {
    Code int         `json:"code"`
    Data interface{} `json:"data"`
    Msg  string      `json:"msg"`
}

type UserInfo {
    UserId   uint   `json:"user_id"`
    Username string `json:"username"`
}

type UserInfoResponse {
    Code int      `json:"code"`
    Data UserInfo `json:"data"`
    Msg  string   `json:"msg"`
}

service users {
    // 这里 @handler 指定 包的名字 loginlogic
    @handler login
    post /api/users/login (LoginRequest) returns (LoginResponse)

    @handler UserInfo
    get /api/users/info returns (UserInfoResponse)
}

// goctl api go -api user.api -dir .

# 贡献
欢迎贡献代码和提出建议！请访问 GitHub 仓库 提交问题和拉取请求。
