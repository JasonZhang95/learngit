# FlexiCache

## 概念

### App ID 的歧义与解决

在不加说明的情况下，本项目中的 `AppID` 有如下两种含义：

1. 公司业务上有 `AppID` 的概念，是一个应用的全网唯一标识符，是字符串，例如 `biz.booking`, `corvus.apollo_query_cache`

2. 本项目中有名为 `apps` 的表，其他表存在 `app_id` 字段，用来表示与 `apps` 表的关联关系，是个整数

为了避免歧义，做如下定义：

| 关键字 | 含义 | 称呼 |
|-------|-----|------|
| 本项目中所有形式的 `app_id`   | `apps` 表中的 `ID` 字段 | 应用编号 |
| 本项目中所有形式的 `app_name` | 公司业务上的 `AppID` 对应 `apps` 表中的 `name` 字段 | 应用名称 |

为了与公司同事的认知对齐，在给人类使用的 UI 上应该继续使用 `AppID` 来表示本项目中的 `app_name`，预计前端代码不会出现在本仓库中，因此此举与上述定义不矛盾。

## 编码约定

### 测试

- 只在测试中使用的函数前缀 `_`

### Model

1. 返回复数个实体的函数用 `Query` 开头，例如 `QueryByName`，单数用 `Get` 开头，例如 `GetByID`


## Controller manual

### start & stop

Use systemd to manage the FlexiCache controller processs.

```

# start fc-ctl process
systemctl start fc-ctl.service

# stop fc-ctl process
systemctl stop fc-ctl.service
```

## Requirements
### 开发
- 安装`go`和`git`，配置好`GOPATH`等路径
- 将主仓库的`master`分支`fork`到个人仓库，
  再`clone`到本地进行开发，具体工作流可参考[Workflow](https://github.com/xirong/my-git/blob/master/git-workflow-tutorial.md)
- 注意每次`commit`的`Message`内容是否得当，可参考[How to Write a Git Commit Message](https://chris.beams.io/posts/git-commit/#separate)
- 每次Merge Request之前要在本地进行单元测试

### 测试
- 本地进行单元测试需要安装配置好`MySQL`和`Redis`，然后在本地`FlexiCache`目录下运行命令`make test`
- 如果本地未安装`MySQL`和`Redis`，可以安装`docker`,然后直接在本地`FlexiCache`目录下运行命令`make docker-test`
