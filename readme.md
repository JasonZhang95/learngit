# FlexiCache
## Requirements
### 开发
- 安装`go`和`git`，配置好`GOPATH`等路径
- 将主仓库的`master`分支`fork`到个人仓库，
  再`clone`到本地进行开发，具体工作流可参考[Workflow]https://github.com/xirong/my-git/blob/master/git-workflow-tutorial.md
- 注意每次`commit`的`Message`内容是否得当，可参考[How to Write a Git Commit Message] https://chris.beams.io/posts/git-commit/#separate
- 每次Merge Request之前要在本地进行单元测试

### 测试
- 本地进行单元测试需要安装配置好`MySQL`和`Redis`，然后在本地`FlexiCache`目录下运行命令`make test`
- 如果本地未安装`MySQL`和`Redis`，可以安装`docker`,然后直接在本地`FlexiCache`目录下运行命令`make docker-test`
