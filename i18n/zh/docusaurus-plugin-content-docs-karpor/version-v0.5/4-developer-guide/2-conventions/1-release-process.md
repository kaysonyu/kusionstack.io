---
title: 发布流程和节奏
---
## 发布计划

我们将通过 [GitHub 里程碑](https://github.com/KusionStack/karpor/milestones) 建立并持续根据发布计划。每个发布里程碑将包括两类任务：

- Maintainer 承诺完成的任务。Maintainer 会在根据他们的时间和精力承诺下次发布要实现的特性。通常，这些任务会经过离线讨论并添加到里程碑。这些任务会被分配给计划实施和测试它们的 Maintainer。
- Contributor 提出的额外事项，通常是不紧急的特性和优化。Maintainer 不承诺在当前 release 周期内完成，但承诺会对这些社区提交进行代码审查。

里程碑会清晰地描述最终要的特性和期望完成日期。这将清楚地告知终端用户下一版本的发布时间和内容。

除了下一次里程碑之外，我们也会维护未来几个发布里程碑的草稿。

## 发布标准

- 所有的 **官方发布** 都应该在 `main` 分支添加标签，并且携带类似 `alpha`、 `beta`、 `rc` 的可选先行版本后缀，例如，一个通常的官方发布版本可能是 `v1.2.3`、 `v1.2.3-alpha.0`。例如，如果我们想要在发布正式版本 `v1.2.3` 之前进行一些验证，我们可以先发布类似 `v1.2.3-alpha.0` 的先行版本，在验证完成之后再发布 `v1.2.3` 版本。
- Maintainer 承诺完成特定的特性和增强，由 [GitHub 里程碑](https://github.com/KusionStack/karpor/milestones) 跟踪。
- 我们会尽可能防止发布延期；如果一个特性无法按时完成，它将会被挪到下次发布。
- **每月** 发布一个新版本。

## 发布标准流程

Maintainer 负责推动发布过程并遵循标准操作程序以确保发布的质量。

1. 为指定发布的 git commit 添加标签并推到上游；该标签需要满足[语义化版本控制](#%E8%AF%AD%E4%B9%89%E5%8C%96%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6)。
2. 确保触发的 Github Action 流水线执行成功。一旦成功，将会自动触发一次 Github 发布，其中包括根据提交信息计算出的 Changelog，以及镜像和 tar.gz 文件等制品。
3. 根据 **Github 发布** 编写清晰的发布说明，包括：
   - 用户友好的发布亮点。
   - 已弃用和不兼容的更改。
   - 有关如何安装和升级的简要说明。

## 门控测试

在创建发布分支之前：我们会有一个 **一周** 的代码冻结期。在这期间，我们将避免合并任何功能 PR，只会修复错误。

Maintainer 会负责测试并修复那些在临近发布时间发现的紧急问题。

## 语义化版本控制

`Karpor` 采用 [语义化版本控制](https://semver.org/lang/zh-CN/) 作为版本号。

版本格式为：主版本号.次版本号.修订号，例如， `v1.2.3`。版本号  **递增规则** 如下：

- 主版本号：当你做了不兼容的 API 修改。
- 次版本号：当你做了向下兼容的功能性新增。
- 修订号：当你做了向下兼容的问题修正。

**先行版本号及版本编译信息** 可以作为加到“主版本号.次版本号.修订号”的后面，作为延伸，比如 `v1.2.3-alpha.0`, `v1.2.3-beta.1`, `v1.2.3-rc.2`, 其中 `-alpha.0`, `-beta.1`, `-rc.2` 是先行版本号。