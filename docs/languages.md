# 语言项目

本页统一维护语言项目入口。各语言的实现方式、功能范围和发行节奏可以不同，不能从其他语言或上游项目推断某个 Beacon 版本的支持能力。

未来接入新语言时，先参考[新语言接入与首次发行经验](language-onboarding.md)确定维护方式和验证边界；未建立的工程不在此页提供占位仓库或安装入口。

## Java

采用完整 OpenTelemetry Java Instrumentation 源码的下游维护方式，保留上游历史，并在对应模块开发自有增强。当前处于工程准备阶段，尚无 Beacon Java 正式发行。

以下开发入口已推送到 GitHub，使用 `main` 开发分支。开发文档会随分支更新，不作为正式版本的安装或支持承诺。

| 入口 | 开发地址 |
| --- | --- |
| 源码仓库 | [beacon-observability/beacon-java](https://github.com/beacon-observability/beacon-java) |
| 开发说明 | [Beacon Java 开发入口](https://github.com/beacon-observability/beacon-java/blob/main/beacon/README.md) |
| 源码来源 | [上游基线记录](https://github.com/beacon-observability/beacon-java/blob/main/beacon/upstream.lock.json) |
| 上游维护 | [OTel 同步流程](https://github.com/beacon-observability/beacon-java/blob/main/beacon/UPSTREAM.md) |
| 发行开发 | [发行流程与准备项](https://github.com/beacon-observability/beacon-java/blob/main/beacon/RELEASING.md) |

上述链接指向开发文档，会随开发分支变化，不代表某个正式版本的安装指南或支持承诺。首次发行后，本页再补充实际发布标签对应的使用文档与 Release 链接。

## .NET

采用完整 OpenTelemetry .NET Automatic Instrumentation 源码的独立下游维护方式，不使用 GitHub Fork。当前正式版本为 `0.1.4`，提供 Linux glibc/musl、Windows、macOS 和 NuGet 归档，并附带安装脚本、校验和、SPDX SBOM 与构建证明。DataKit 接收链路尚未纳入已验证支持范围，具体能力和限制以版本说明为准。

| 入口 | 地址 |
| --- | --- |
| 源码仓库 | [beacon-observability/beacon-dotnet](https://github.com/beacon-observability/beacon-dotnet) |
| 开发说明 | [Beacon .NET 开发入口](https://github.com/beacon-observability/beacon-dotnet/blob/main/beacon/README.md) |
| 源码来源 | [上游基线记录](https://github.com/beacon-observability/beacon-dotnet/blob/main/beacon/upstream.lock.json) |
| 上游维护 | [同步流程](https://github.com/beacon-observability/beacon-dotnet/blob/main/beacon/UPSTREAM.md) |
| 当前发行 | [Beacon .NET 0.1.4](https://github.com/beacon-observability/beacon-dotnet/releases/tag/beacon-v0.1.4) |

## Go

计划在 `beacon-observability/beacon-go` 维护。工程尚待建立，先盘点现有实现并确定维护方式；暂不提供仓库或安装链接。

## Python

采用完整 OpenTelemetry Python Contrib 源码的独立下游维护方式，不使用 GitHub Fork。开发工程已从旧 `gtrace` 分支保留自有增强与提交历史，并合入官方 `v0.65b0` 发布基线；配套 Python Core 开发依赖固定到 `v1.44.0`。旧 `gtrace` 发行包已移除，`beacon-otel` 主包与可选的 `beacon-profiling` 开发包已实现；本地单元测试和 Python 3.10–3.14 独立环境安装及启动冒烟测试已完成，完整上游矩阵、DataKit 后端入库确认和正式候选制品验收尚未完成，因此仍无 Beacon Python 正式发行或安装入口。

以下开发入口已推送到 GitHub，使用 `main` 开发分支。开发文档会随分支更新，不作为正式版本的安装或支持承诺。

| 入口 | 开发地址 |
| --- | --- |
| 源码仓库 | [beacon-observability/beacon-python](https://github.com/beacon-observability/beacon-python) |
| 开发说明 | [Beacon Python 开发入口](https://github.com/beacon-observability/beacon-python/blob/main/beacon/README.md) |
| 源码来源 | [上游基线记录](https://github.com/beacon-observability/beacon-python/blob/main/beacon/upstream.lock.json) |
| 上游维护 | [OTel 同步流程](https://github.com/beacon-observability/beacon-python/blob/main/beacon/UPSTREAM.md) |
| 发行准备 | [发行准备项](https://github.com/beacon-observability/beacon-python/blob/main/beacon/RELEASING.md) |

现有自有实现的来源已保留在 `beacon-python` 的 Git 历史中；已有旧版 PyPI 包不等于 Beacon Python 发行。首次发行后，本页再补充固定版本的安装与 Release 链接。

## PHP

PHP 分为两个非 Fork 下游仓库：`beacon-php` 保留 OpenTelemetry PHP Contrib 完整历史，维护组件插桩和 Composer 聚合包；`beacon-php-instrumentation` 保留官方原生扩展完整历史，并合入 GuanceCloud 旧 `gtrace` 分支用于追溯跨平台构建与制品经验。两者通过固定提交联调，手动插桩不强制加载扩展。当前原生扩展已通过 Linux、macOS、Windows 代表性矩阵、PHPT 和源码包构建，Composer 包已在 PHP 8.2/8.4 从固定扩展提交安装及诊断联调；完整组件矩阵、实际接收端链路及正式制品发布尚未完成，因此仍无 Beacon PHP 正式发行或安装入口。

以下开发入口已推送到 GitHub `main` 分支。文档会随开发进展更新，不作为正式版本的安装或支持承诺。

| 入口 | 开发地址 |
| --- | --- |
| 源码仓库 | [beacon-observability/beacon-php](https://github.com/beacon-observability/beacon-php) |
| 原生扩展仓库 | [beacon-observability/beacon-php-instrumentation](https://github.com/beacon-observability/beacon-php-instrumentation) |
| 开发说明 | [Beacon PHP 开发入口](https://github.com/beacon-observability/beacon-php/blob/main/beacon/README.md) |
| 源码来源 | [上游基线记录](https://github.com/beacon-observability/beacon-php/blob/main/beacon/upstream.lock.json) |
| 上游维护 | [OTel 同步流程](https://github.com/beacon-observability/beacon-php/blob/main/beacon/UPSTREAM.md) |
| 发行准备 | [发行准备项](https://github.com/beacon-observability/beacon-php/blob/main/beacon/RELEASING.md) |
| 扩展工程说明 | [Beacon PHP Instrumentation 开发入口](https://github.com/beacon-observability/beacon-php-instrumentation/blob/main/beacon/README.md) |
| 扩展来源 | [扩展双来源基线](https://github.com/beacon-observability/beacon-php-instrumentation/blob/main/beacon/upstream.lock.json) |

首次发行后，本页再补充固定版本的安装与 Release 链接。

## 支持范围的维护方式

正式发行后，各语言的版本文档负责列出已验证的遥测与增强能力、运行环境、接收端兼容范围、已知限制及升级回退方法。

本仓库需要跨语言对比时，只汇总带有明确版本和证据链接的能力状态，不复制完整运行矩阵。涉及 DataKit 的接入，以实际验证的版本和协议为准。源码存在、构建成功或上游支持均不能单独作为 Beacon 已支持的依据。
