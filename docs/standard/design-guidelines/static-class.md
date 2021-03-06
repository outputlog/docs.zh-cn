---
title: 静态类设计
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 104fa204a95ef31d34e224348068e3a6505aded5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743591"
---
# <a name="static-class-design"></a>静态类设计
静态类定义为仅包含静态成员的类（当然，除了从 <xref:System.Object?displayProperty=nameWithType> 继承的实例成员，还可能是私有构造函数）。 某些语言提供对静态类的内置支持。 在 C# 2.0 及更高版本中，当类声明为静态时，它是密封、抽象的，并且不能覆盖或声明实例成员。

 静态类是纯面向对象设计和简单性之间的妥协。 它们通常用于提供对其他操作（如 <xref:System.IO.File?displayProperty=nameWithType>）、扩展方法的持有者或功能的快捷方式，以便为其有人完全面向对象的包装器（如 <xref:System.Environment?displayProperty=nameWithType>）。

 ✔️尽量少使用静态类。

 静态类应仅用作框架的面向对象核心的支持类。

 ❌ 不要将静态类视为其他存储桶。

 ❌ 不声明或重写静态类中的实例成员。

 如果你的编程语言没有对静态类的内置支持，✔️会将静态类声明为密封、抽象并添加私有实例构造函数。

 *部分©2005，2009 Microsoft Corporation。保留所有权利。*

 *在 Pearson Education, Inc. 授权下，由 Addison-Wesley Professional 作为 Microsoft Windows 开发系列的一部分再版自 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)（Framework 设计准则：可重用 .NET 库的约定、惯例和模式第 2 版），由 Krzysztof Cwalina 和 Brad Abrams 发布于 2008 年 10 月 22 日。

## <a name="see-also"></a>另请参阅

- [类型设计准则](../../../docs/standard/design-guidelines/type.md)
- [框架设计指南](../../../docs/standard/design-guidelines/index.md)
