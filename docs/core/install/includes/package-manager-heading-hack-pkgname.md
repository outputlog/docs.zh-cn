---
ms.openlocfilehash: 4340ed7444681b4601dea50c93926b0ee0c07eec
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134107"
---

添加到包管理器源的包以可改动的格式命名：`{product}-{type}-{version}`。

- **product**\
要安装的 .NET 产品的类型。 有效选项是：

  - dotnet
  - aspnetcore

- **type**\
选择 SDK 或运行时。 有效选项是：

  - SDK
  - Runtime — 运行时

- **version**\
要安装的 SDK 或运行时的版本。 本文始终提供最新支持的版本的说明。 有效选项为任何已发布的版本，例如：

  - 3.1
  - 3.0
  - 2.1

  尝试下载的 SDK/运行时可能不适用于 Linux 发行版。 有关受支持的发行版的列表，请参阅 [.NET Core 依赖项和要求](../dependencies.md?pivots=os-linux)。

### <a name="examples"></a>示例

- 安装 ASP.NET Core 3.1 运行时：`aspnetcore-runtime-3.1`
- 安装 .NET Core 2.1 运行时：`dotnet-runtime-2.1`
- 安装 .NET Core 3.1 SDK：`dotnet-sdk-3.1`

### <a name="package-missing"></a>缺少包

如果包版本组合无效，则它不可用。 例如，未安装 ASP.NET Core SDK，所有 SDK 组件都包含在 .NET Core SDK 中。 `aspnetcore-sdk-2.2` 的值不正确，应为 `dotnet-sdk-2.2`。 有关 .NET Core 支持的 Linux 发行版的列表，请参阅 [.NET Core 依赖项和要求](../dependencies.md?pivots=os-linux)。
