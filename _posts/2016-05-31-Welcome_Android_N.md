---
layout: post
title: Welcome Android N
categories: [android]
tags: [reachzhai, android, welcome]
description: Android N Preview 
---

**N Developer Preview 从 2016 年 3 月 9 日开始使用，到向 AOSP 和 OEM 公开发布最终 Android N 时停止使用，预计将于 2016 年第三季度发布最终版本。**

在开发阶段的各个里程碑，我们将为您的开发和测试环境提供更新。一般每月（间隔 4 到 6 周）会提供一次更新。里程碑列表如下。

>  - Preview 1（初始版本，alpha） 
>  - Preview 2（增量更新，beta）
>  - Preview 3（增量更新，beta）
>  - Preview 4（最终 API 和官方 SDK，在 Play 中发布）
>  - Preview 5（接近最终版本系统映像，用于最终测试）

向 AOSP 和生态系统发布最终版本
每次的更新包括 SDK 工具、预览版系统映像、模拟器、参考文档和 API 差异。

**N Developer Preview 包含的内容**

N Developer Preview 包括您在各种使用不同屏幕尺寸、网络技术、CPU/GPU 芯片组和硬件架构的设备中测试现有应用所需的所有功能。

**SDK 工具**
您可通过 Android Studio 中的 SDK 管理器下载这些组件：

> - N Developer Preview SDK 和工具
> - N Developer Preview 模拟器系统映像（32 位和 64 位）
> - 适用于 Android TV 的 N Developer Preview模拟器系统映像（32 位）
> - N Developer Preview 支持库（用于新应用模板）

我们将根据需要在每个里程碑为这些开发工具提供更新。

**硬件系统映像**
N Developer Preview 包含 Nexus 以及可用于在物理设备上进行测试和开发的其他硬件系统映像。如需了解硬件映像的完整列表，请参阅设备映像页面。

我们将在每个里程碑为这些设备提供更新的系统映像。您可以手动下载更新的系统映像，并刷入测试设备（如需要，可多次刷入）。这尤其适合需要多次重刷设备的自动化测试环境。

> 注：手动刷入设备将不会像在去年的预览版中一样获得 OTA 更新。今年，您可以通过在 Android Beta 计划中注册设备获得 OTA —
> 有关详情请参阅下文。

**通过 Android Beta 计划获得 OTA 更新**
Android N 的一项新功能是空中下载 (OTA) 更新计划，该功能可以将 Android N 最新的预览版更新直接发送到注册该计划的设备。该计划是免费服务，只要您拥有支持的设备并将其注册到 Google 帐户，就可以使用该服务。

如需注册该计划，请访问 Android Beta 计划网站。您将可以看到您的帐户中所有可以注册 Android Beta 的设备。

> 选择用于接收 Android N 更新的设备 点击 Enroll，查看并同意服务条款，然后点击 OK。
> 注册完成后，您的设备将很快收到更新。多数情况下，切换到 Android N
> 不需要重置所有数据，但建议您在注册设备前对重要数据进行备份，以免丢失。

在设备收到更新后，建议您尽快下载并安装更新，以便在系统 UI、行为、API 和功能中及时同步最新的变更。

在 Developer Preview 结束运行时，您的注册设备将收到官方 Android N 版本的更新。

您可以在 Android Beta 网站上随时注销注册 Android Beta 计划的设备。在注销前，请务必备份设备上的数据。

注：注销后，您的设备将恢复到最新版本 Android 6.0 Marshmallow 的出厂设置（不一定是您注册设备前安装的版本）。为确保全新安装，您设备中的数据将被擦除，包括联系人、消息和照片等。

**文档和示例代码**
Developer Preview 网站上提供的以下文档资源有助于您了解 Android N：

- Android N 开发设置，提供入门指南的分步说明。
- 行为变更，带您了解主要测试领域。
- 新 API 文档，包括 API 概览、可下载的 API 参考资料以及有关主要功能（例如多窗口支持、受限通知、多区域设置支持等）的详细开发者指南。
- 示例代码，演示如何支持权限和其他新功能。
- N Developer Preview 当前版本的版本说明，包括变更说明和差异报告

**可下载的 API 参考资料**
在预览版更新初期，您可以下载最新的 Android N 平台 API 参考资料，作为单独的 Zip 存档。下载的参考资料还包含差异报告，可帮助您识别相对 API 23 和上一次更新 API 的变更。

在确定最终版本 Android N API 并指定正式 API 级别后，我们将在网站 https://developer.android.com 上提供 API 参考资料。

**支持资源**
在 N Developer Preview 中测试和开发时，请使用以下渠道报告问题和提供反馈。

N Developer Preview 的 Issue Tracker 是您的主要反馈渠道。您可通过 Issue Tracker 报告错误、性能问题和一般反馈。您还可以查阅已知问题并找到解决方法。我们将对您的问题进行分类并发送到 Android 工程团队以供审查，且会为您提供进度更新通知。
Android N 开发者社区是一个 Google+ 社区。在此社区中，您可与其他使用 Android N 的开发者建立联系。您可以分享观察结果或想法，或找到 Android N 问题的解决方法。我们将管理社区，并根据需要提供解答和指导。
锁定目标、预览版 API 和发布
N Developer Preview 提供的系统和 Android 库仅面向开发，不具备标准的 API 级别。如果您想通过拒绝兼容性行为测试您的应用（强烈推荐此做法），则可将应用的 targetSdkVersion 设置为 “N”，从而锁定 Android N 的预览版。

Android N Developer Preview 提供预览 API 功能 — 在最终版本 SDK 发布之前，这些 API 都不是正式版本。目前，最终版本 SDK 计划于 2016 年第三季度发布。这意味着一段时期内，特别是该计划的最初几周内，API 可能会出现细微更改。我们会通过 Android N Developer Preview 的每次更新为您提供变更摘要。

> 注：虽然预览版 API 可能会更改，但基本系统行为仍保持稳定，可以立即用于测试。

Google Play 禁止发布面向 N Developer Preview 的应用。当 Android N 最终版本 SDK 可用时，您可以锁定官方 Android N API 级别，并通过 alpha 和 beta 发布渠道将应用发布至 Google Play。与此同时，如果您想要向测试者推广面向 Android N 的应用，则可通过电子邮件或从您的站点直接下载来实现。

在向 AOSP 和 OEM 全面发布 Android N 后（计划在 2016 年第三季度发布），您将可以在 Google Play 的公开发布渠道发布面向 Android N 的应用。

**入门指南**
在使用 Android N 测试应用前，请执行以下操作：

- 查看 [API 概览](https://developer.android.com/preview/api-overview.html)和[行为变更](https://developer.android.com/preview/behavior-changes.html)，大致了解新功能及其对您应用的影响。您尤其需要了解的是新的通知功能和多窗口支持。
- 根据设置 [Preview SDK 和配置测试设备](https://developer.android.com/preview/setup-sdk.html)的说明设置您的环境。
- 根据刷入说明，对设备刷入最新的 Android N 系统映像。
- 查阅 [API 参考资料](https://developer.android.com/preview/setup-sdk.html#docs-dl)和 [Android N 示例](https://developer.android.com/preview/samples.html)，更深入地了解新 API 功能以及如何在应用中使用这些功能。
- 加入 [Android N 开发者社区](https://plus.google.com/communities/103655397235276743411)，获取最新资讯，并与使用新平台的其他开发者建立联系。

感谢您加入 Android N Developer Preview 计划！

