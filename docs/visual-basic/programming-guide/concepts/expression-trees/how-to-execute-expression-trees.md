---
title: 'Nasıl yapılır: (Visual Basic) ifade ağaçlarını yürütme'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 62d3febf7090c6662e5593bbaf94c04236a162e9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592145"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="2a36e-102">Nasıl yapılır: (Visual Basic) ifade ağaçlarını yürütme</span><span class="sxs-lookup"><span data-stu-id="2a36e-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="2a36e-103">Bu konu nasıl bir ifade ağacı çalıştırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2a36e-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="2a36e-104">İfade ağacı yürütülürken bir değer döndürebilir veya sadece bir yöntemi gibi bir eylem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="2a36e-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="2a36e-105">Lambda ifadeleri temsil eden ifade ağaçları çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2a36e-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="2a36e-106">Lambda ifadeleri temsil eden ifade ağaçları, tür <xref:System.Linq.Expressions.LambdaExpression> veya <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="2a36e-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="2a36e-107">Bu ifade ağaçlarını yürütme için çağrı <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> yürütülebilir bir temsilci oluşturmak ve ardından temsilci çağırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="2a36e-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a36e-108">Metot temsilcisinin türü bilinmiyor, diğer bir deyişle, lambda ifadesi türü ise <xref:System.Linq.Expressions.LambdaExpression> değil <xref:System.Linq.Expressions.Expression%601>, çağırmalısınız <xref:System.Delegate.DynamicInvoke%2A> yöntemini doğrudan çağırmak yerine temsilci.</span><span class="sxs-lookup"><span data-stu-id="2a36e-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="2a36e-109">Bir lambda ifadesi ifade ağacına temsil etmiyorsa çağırarak orijinal ifade ağacı, gövdeye, sahip yeni bir lambda ifadesi oluşturabilirsiniz <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2a36e-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="2a36e-110">Ardından, lambda ifadesi bu bölümde daha önce açıklanan şekilde yürütebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2a36e-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a36e-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a36e-111">Example</span></span>  
 <span data-ttu-id="2a36e-112">Aşağıdaki kod örneği, bir lambda ifadesi oluşturma ve yürütme güç bir sayıya yükseltme temsil eden bir ifade ağacı yürütülecek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2a36e-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="2a36e-113">Oluşturulan sayı gücünü temsil eder, sonuç görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2a36e-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```vb  
' The expression tree to execute.  
Dim be As BinaryExpression = Expression.Power(Expression.Constant(2.0R), Expression.Constant(3.0R))  
  
' Create a lambda expression.  
Dim le As Expression(Of Func(Of Double)) = Expression.Lambda(Of Func(Of Double))(be)  
  
' Compile the lambda expression.  
Dim compiledExpression As Func(Of Double) = le.Compile()  
  
' Execute the lambda expression.  
Dim result As Double = compiledExpression()  
  
' Display the result.  
MsgBox(result)  
  
' This code produces the following output:  
' 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2a36e-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="2a36e-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="2a36e-115">System.Linq.Expressions ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="2a36e-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a36e-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a36e-116">See also</span></span>

- [<span data-ttu-id="2a36e-117">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a36e-117">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="2a36e-118">Nasıl yapılır: (Visual Basic) ifade ağaçlarını değiştirme</span><span class="sxs-lookup"><span data-stu-id="2a36e-118">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
