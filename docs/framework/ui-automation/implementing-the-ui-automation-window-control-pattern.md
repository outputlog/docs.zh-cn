---
title: 实现 UI 自动化 Window 控件模式
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
ms.openlocfilehash: dd677ca9f610d463acc7c69f99767bd7b8781589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180037"
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a>实现 UI 自动化 Window 控件模式
> [!NOTE]
> 本文档适用于想要使用 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 命名空间中定义的托管 <xref:System.Windows.Automation> 类的 .NET Framework 开发人员。 有关 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]的最新信息，请参阅 [Windows 自动化 API：UI 自动化](/windows/win32/winauto/entry-uiauto-win32)。  
  
 本主题介绍实现 <xref:System.Windows.Automation.Provider.IWindowProvider>的准则和约定，包括有关 <xref:System.Windows.Automation.WindowPattern> 属性、方法和事件的信息。 本主题的结尾列出了指向其他参考资料的链接。  
  
 控件<xref:System.Windows.Automation.WindowPattern>模式用于支持在传统图形用户界面 （GUI） 中提供基于窗口的基本功能的控件。 必须实现此控制模式的控件示例包括顶级应用程序窗口、多文档接口 （MDI） 子窗口、可调整大小的拆分窗格控件、模式对话框和气球帮助窗口。  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>实现准则和约定  
 在实现 Window 控件模式时，请注意以下准则和约定：  
  
- 为了能够使用 UI 自动化同时修改窗口大小和屏幕位置，除了 <xref:System.Windows.Automation.Provider.ITransformProvider> 外，控件还必须实现 <xref:System.Windows.Automation.Provider.IWindowProvider>。  
  
- 包含标题栏和标题栏元素（使控件能够移动、调整大小、最大化、最小化或关闭）的控件通常需要实现 <xref:System.Windows.Automation.Provider.IWindowProvider>。  
  
- 诸如工具提示弹出窗口以及组合框或下拉菜单之类的控件通常不实现 <xref:System.Windows.Automation.Provider.IWindowProvider>。  
  
- 气球状帮助窗口和基本工具提示弹出窗口的区别在于是否提供了像窗口一样的“关闭”按钮。  
  
- IWindowProvider 不支持全屏模式，因为它是特定于应用程序的功能，而不是典型的窗口行为。  
  
<a name="Required_Members_for_IWindowProvider"></a>
## <a name="required-members-for-iwindowprovider"></a>IWindowProvider 必需的成员  
 IWindowProvider 接口需要以下属性、方法和事件。  
  
|必需的成员|成员类型|说明|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|properties|无|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|properties|无|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|properties|无|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|properties|无|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|properties|无|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|properties|无|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|方法|无|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|方法|无|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|方法|无|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|事件|无|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|事件|无|  
|<xref:System.Windows.Automation.WindowInteractionState>|事件|不保证为 <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction>|  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>例外  
 提供程序必须引发以下异常。  
  
|异常类型|条件|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> - 当控件不支持请求的行为时。|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> - 当参数不是有效数字时。|  
  
## <a name="see-also"></a>另请参阅

- [UI 自动化控件模式概述](ui-automation-control-patterns-overview.md)
- [在 UI 自动化提供程序中支持控件模式](support-control-patterns-in-a-ui-automation-provider.md)
- [客户端的 UI 自动化控件模式](ui-automation-control-patterns-for-clients.md)
- [UI 自动化树概述](ui-automation-tree-overview.md)
- [在 UI 自动化中使用缓存](use-caching-in-ui-automation.md)
