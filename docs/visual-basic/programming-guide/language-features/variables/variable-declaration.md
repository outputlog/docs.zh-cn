---
title: 变量声明
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables [Visual Basic], declarations
- Dim statement [Visual Basic], variable declaration
- declaring variables [Visual Basic]
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime [Visual Basic], variables
- variables [Visual Basic], lifetime
- access levels [Visual Basic], variables
- scope [Visual Basic], declaration statements
- variables [Visual Basic], access level
- local variables [Visual Basic], declarations
- scope [Visual Basic], variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
ms.openlocfilehash: b89773e9527af0d65cde53b61654f2511f5c8dde
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351766"
---
# <a name="variable-declaration-in-visual-basic"></a>Visual Basic 中的变量声明
声明一个变量来指定其名称和特征。 变量的声明语句是[Dim 语句](../../../../visual-basic/language-reference/statements/dim-statement.md)。 其位置和内容确定变量的特征。  
  
 有关变量命名规则和注意事项，请参阅已[声明的元素名称](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)。  
  
## <a name="declaration-levels"></a>声明级别  
  
### <a name="local-and-member-variables"></a>局部变量和成员变量  
 局部变量是在过程中声明的*变量*。 *成员变量*是 Visual Basic 类型的成员;它在模块级别、类、结构或模块中声明，但不在该类、结构或模块内部的任何过程中声明。  
  
### <a name="shared-and-instance-variables"></a>共享变量和实例变量  
 在类或结构中，成员变量的类别取决于它是否是共享的。 如果使用[shared](../../../../visual-basic/language-reference/modifiers/shared.md)关键字进行声明，则它是*共享变量*，并且存在于在类或结构的所有实例中共享的单个副本。  
  
 否则，它是一个*实例变量*，为类或结构的每个实例创建一个单独的副本。 实例变量的给定副本仅可用于创建它的类或结构的实例。 它与类或结构的任何其他实例中的实例变量副本无关。  
  
## <a name="declaring-data-type"></a>声明数据类型  
 声明语句中的[As](../../../../visual-basic/language-reference/statements/as-clause.md)子句允许您定义要声明的变量的数据类型或对象类型。 您可以为变量指定以下任意类型：  
  
- 基本数据类型，如 `Boolean`、`Long`或 `Decimal`  
  
- 复合数据类型，例如数组或结构  
  
- 在应用程序或其他应用程序中定义的对象类型或类  
  
- .NET Framework 类，如 <xref:System.Windows.Forms.Label> 或 <xref:System.Windows.Forms.TextBox>  
  
- 接口类型，如 <xref:System.IComparable> 或 <xref:System.IDisposable>  
  
 您可以在一个语句中声明多个变量，而不必重复该数据类型。 在下面的语句中，将 `i`、`j`和 `k` 的变量声明为类型 `Integer`，将 `l` 和 `m` 作为 `Long`进行声明，并将 `x` 和 `y` 视为 `Single`：  
  
```vb  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 有关数据类型的详细信息，请参阅[数据类型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)。 有关对象的详细信息，请参阅[对象和类](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)和[对组件进行编程](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/0ffkdtkf(v=vs.120))。  
  
## <a name="local-type-inference"></a>局部类型推理  
 *类型推理*用于确定不使用 `As` 子句声明的局部变量的数据类型。 编译器从初始化表达式的类型推断出变量的类型。 这样，便可以在不显式声明类型的情况下声明变量。 在下面的示例中，`num1` 和 `num2` 都作为整数强类型化。  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
  
 如果要使用局部类型推理，则必须将 `Option Infer` 设置为 `On`。 有关详细信息，请参阅[本地类型推断](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)和 [Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)。  
  
## <a name="characteristics-of-declared-variables"></a>声明变量的特征  
 变量的*生存期*是指可供使用的时间段。 一般情况下，只要声明该变量的元素（如过程或类）继续存在，就会存在该变量。 如果变量不需要在其包含元素的生存期之外继续存在，则无需在声明中执行任何特殊操作。 如果变量的长度需要大于其包含元素，则可以在其 `Dim` 语句中包含 `Static` 或 `Shared` 关键字。 有关详细信息，请参阅[Visual Basic 中的生存期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)。  
  
 变量的*作用域*是指可以引用它的所有代码的集合，而无需限定其名称。 变量的作用域由声明它的位置确定。 位于给定区域的代码可以使用该区域中定义的变量，而不必限定其名称。 有关详细信息，请参阅 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)。  
  
 变量的*访问级别*是有权访问它的代码的范围。 这由您在 `Dim` 语句中使用的访问修饰符（如[Public](../../../../visual-basic/language-reference/modifiers/public.md)或[Private](../../../../visual-basic/language-reference/modifiers/private.md)）确定。 有关详细信息，请参阅[Visual Basic 中的访问级别](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="see-also"></a>另请参阅

- [如何：创建新变量](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)
- [如何：将数据移入和移出变量](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [数据类型](../../../../visual-basic/language-reference/data-types/index.md)
- [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)
- [Static](../../../../visual-basic/language-reference/modifiers/static.md)
- [已声明元素的特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [局部类型推理](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer 语句](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
