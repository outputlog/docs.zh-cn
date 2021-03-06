---
title: dotnet publish 命令
description: dotnet publish 命令可将 .NET Core 项目或解决方案发布到目录。
ms.date: 02/24/2020
ms.openlocfilehash: 0e18220443f3713c86c257fcf401b98ddd716ebc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588270"
---
# <a name="dotnet-publish"></a>dotnet publish

 本文适用于： ✔️ .NET Core 2.1 SDK 及更高版本

## <a name="name"></a>“属性”

`dotnet publish` - 将应用程序及其依赖项发布到文件夹以部署到托管系统。

## <a name="synopsis"></a>摘要

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a>描述

`dotnet publish` 编译应用程序、读取 project 文件中指定的所有依赖项并将生成的文件集发布到目录。 输出包括以下资产：

- 扩展名为 dll  的程序集中的中间语言 (IL) 代码。
- 包含项目所有依赖项的 .deps.json 文件  。
- .runtimeconfig.json 文件，其中指定了应用程序所需的共享运行时，以及运行时的其他配置选项（例如垃圾回收类型）  。
- 应用程序的依赖项，将这些依赖项从 NuGet 缓存复制到输出文件夹。

`dotnet publish` 命令的输出可供部署至托管系统（例如服务器、电脑、Mac、笔记本电脑）以便执行。 若要准备用于部署的应用程序，这是唯一正式受支持的方法。 根据项目指定的部署的类型，托管系统不一定已在其上安装 .NET Core 共享运行时。 有关详细信息，请参阅[使用 .NET Core CLI 发布 .NET Core 应用](../deploying/deploy-with-cli.md)。

### <a name="msbuild"></a>MSBuild

`dotnet publish` 命令调用 MSBuild，后者会调用 `Publish` 目标。 任何传递给 `dotnet publish` 的参数都将传递给 MSBuild。 `-c` 和 `-o` 参数分别映射到 MSBuild 的 `Configuration` 和 `OutputPath` 属性。

`dotnet publish` 命令接受 MSBuild 选项，如用来设置属性的 `-p` 和用来定义记录器的 `-l`。 例如，可以使用以下格式设置 MSBuild 属性：`-p:<NAME>=<VALUE>`。 还可以通过引用 .pubxml  文件来设置与发布相关的属性，例如：

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

有关更多信息，请参见以下资源：

- [MSBuild 命令行参考](/visualstudio/msbuild/msbuild-command-line-reference)
- [用于 ASP.NET Core 应用部署的 Visual Studio 发布配置文件 (.pubxml)](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)

## <a name="arguments"></a>自变量

- **`PROJECT|SOLUTION`**

  要发布的项目或解决方案。
  
  * `PROJECT` 是 [C#](csproj.md)、F# 或 Visual Basic 项目文件的路径和文件名，或包含 C#、F# 或 Visual Basic 项目文件的目录的路径。 如果未指定目录，则默认为当前目录。

  * `SOLUTION` 是解决方案文件（扩展名为 .sln）的路径和文件名，或包含解决方案文件的目录的路径  。 如果未指定目录，则默认为当前目录。 自 .NET Core 3.0 SDK 起可用。

## <a name="options"></a>选项

- **`-c|--configuration <CONFIGURATION>`**

  定义生成配置。 大多数项目的默认配置为 `Debug`，但你可以覆盖项目中的生成配置设置。

- **`-f|--framework <FRAMEWORK>`**

  为指定的[目标框架](../../standard/frameworks.md)发布应用程序。 必须在项目文件中指定目标框架。

- **`--force`**

  强制解析所有依赖项，即使上次还原已成功，也不例外。 指定此标记等同于删除 project.assets.json 文件  。

- **`-h|--help`**

  打印出有关命令的简短帮助。

- **`--interactive`**

  允许命令停止并等待用户输入或操作。 例如，完成身份验证。 自 .NET Core 3.0 SDK 起可用。

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  指定一个或多个[目标清单](../deploying/runtime-store.md)，用于剪裁与应用程序一同发布的一组包。 清单文件是 [`dotnet store` 命令](dotnet-store.md)输出的一部分。 若要指定多个清单，请为每个清单添加一个 `--manifest` 选项。

- **`--no-build`**

  发布前不生成项目。 还将隐式设置 `--no-restore` 标记。

- **`--no-dependencies`**

  忽略项目间引用，仅还原根项目。

- **`--nologo`**

  不显示启动版权标志或版权消息。 自 .NET Core 3.0 SDK 起可用。

- **`--no-restore`**

  运行此命令时不执行隐式还原。

- **`-o|--output <OUTPUT_DIRECTORY>`**

  指定输出目录的路径。
  
  如果未指定，则默认为依赖于运行时的可执行文件和跨平台二进制文件的路径 [project_file_folder]./bin/[configuration]/[framework]/publish/  。 默认为独立的可执行文件路径 [project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/  。

  - .NET Core 3.x SDK 和更高版本
  
    如果在发布项目时指定了相对路径，则生成的输出目录相对于当前工作目录，而不是项目文件位置。

    如果在发布解决方案时指定了相对路径，则所有项目的所有输出都会进入相对于当前工作目录的指定文件夹中。 若要使发布输出进入每个项目的单独文件夹，请使用 msbuild `PublishDir` 属性（而不是 `--output` 选项）指定相对路径。 例如，`dotnet publish -p:PublishDir=.\publish` 将每个项目的发布输出发送到包含项目文件的文件夹下的 `publish` 文件夹中。

  - .NET Core 2.x SDK
  
    如果在发布项目时指定了相对路径，则生成的输出目录相对于项目文件位置，而不是当前工作目录。

    如果在发布解决方案时指定了相对路径，则每个项目的输出会进入相对于项目文件位置的单独文件夹中。 如果在发布解决方案时指定了绝对路径，则所有项目的所有发布输出都会进入指定文件夹中。

- **`--self-contained [true|false]`**

  与应用程序一同发布 .NET Core 运行时，因此无需在目标计算机上安装运行时。 如果指定了运行时标识符，并且项目是可执行项目（而不是库项目），则默认值为 `true`。 有关详细信息，请参阅 [.NET Core 应用程序发布](../deploying/index.md)和[使用 .NET Core CLI 发布 .NET Core 应用](../deploying/deploy-with-cli.md)。

  如果在未指定 `true` 或 `false` 的情况下使用此选项，则默认值为 `true`。 在这种情况下，请不要紧接在 `--self-contained` 后放置解决方案或项目参数，因为该位置需要 `true` 或 `false`。

- **`--no-self-contained`**

  等效于 `--self-contained false`。 自 .NET Core 3.0 SDK 起可用。

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  发布针对给定运行时的应用程序。 有关运行时标识符 (RID) 的列表，请参阅 [RID 目录](../rid-catalog.md)。 有关详细信息，请参阅 [.NET Core 应用程序发布](../deploying/index.md)和[使用 .NET Core CLI 发布 .NET Core 应用](../deploying/deploy-with-cli.md)。

- **`-v|--verbosity <LEVEL>`**

  设置命令的详细级别。 允许使用的值为 `q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]` 和 `diag[nostic]`。 默认值是 `minimal`。

- **`--version-suffix <VERSION_SUFFIX>`**

  定义版本后缀来替换项目文件的版本字段中的星号 (`*`)。

## <a name="examples"></a>示例

- 为当前目录中的项目创建一个 [依赖于运行时的跨平台二进制文件](../deploying/index.md#produce-a-cross-platform-binary)：

  ```dotnetcli
  dotnet publish
  ```

  自 .NET Core 3.0 SDK 起，此示例还为当前平台创建[依赖于运行时的可执行文件](../deploying/index.md#publish-runtime-dependent)。

- 针对特定运行时，为当前目录中的项目创建[独立可执行文件](../deploying/index.md#publish-self-contained)：

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  项目文件中必须包含 RID。

- 针对特定平台，为当前目录中的项目创建[依赖于运行时的可执行文件](../deploying/index.md#publish-runtime-dependent)：

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  项目文件中必须包含 RID。 此示例适用于 .NET Core 3.0 SDK 及更高版本。

- 针对特定运行时和目标框架，在当前目录中发布项目：

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- 发布指定的项目文件：

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- 发布当前应用程序，但在还原操作期间不还原项目到项目 (P2P) 引用，只还原根项目：

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a>请参阅

- [.NET Core 应用程序发布概述](../deploying/index.md)
- [使用 .NET Core CLI 发布 .NET Core 应用](../deploying/deploy-with-cli.md)
- [目标框架](../../standard/frameworks.md)
- [运行时标识符 (RID) 目录](../rid-catalog.md)
- [处理 macOS Catalina 公证](../install/macos-notarization-issues.md)
- [已发布应用程序的目录结构](/aspnet/core/hosting/directory-structure)
- [MSBuild 命令行参考](/visualstudio/msbuild/msbuild-command-line-reference)
- [用于 ASP.NET Core 应用部署的 Visual Studio 发布配置文件 (.pubxml)](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [dotnet msbuild](dotnet-msbuild.md)
