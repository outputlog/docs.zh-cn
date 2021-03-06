---
title: dotnet remove package 命令
description: dotnet remove package 命令可便于删除对项目的 NuGet 包引用。
ms.date: 02/14/2020
ms.openlocfilehash: 8eaa311748c5627351ef149012dc4dddd2ab2793
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503632"
---
# <a name="dotnet-remove-package"></a>dotnet remove package

**本文适用于：** ✔️ .NET Core 2.x SDK 及更高版本

## <a name="name"></a>名称

`dotnet remove package` - 从项目文件删除包引用。

## <a name="synopsis"></a>摘要

```dotnetcli
dotnet remove [<PROJECT>] package <PACKAGE_NAME> [-h|--help]
```

## <a name="description"></a>说明

使用 `dotnet remove package` 命令可方便地从项目删除 NuGet 包引用。

## <a name="arguments"></a>参数

`PROJECT`

指定项目文件。 如果未指定，此命令会搜索当前目录来获取一个项目文件。

`PACKAGE_NAME`

要删除的包引用。

## <a name="options"></a>选项

- **`-h|--help`**

  打印出有关命令的简短帮助。

## <a name="examples"></a>示例

- 从当前目录中的项目删除 `Newtonsoft.Json` NuGet 包：

  ```dotnetcli
  dotnet remove package Newtonsoft.Json
  ```
