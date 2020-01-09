---
title: 'Nasıl Yapılır: İfade Ağaçlarını Yürütme'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 2a2749eaed5279d04b72eb77b066c83de9722fa9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346000"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a><span data-ttu-id="fa56d-102">Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa56d-102">How to: Execute Expression Trees (Visual Basic)</span></span>
<span data-ttu-id="fa56d-103">Bu konu başlığı altında, bir ifade ağacının nasıl yürütüleceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fa56d-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="fa56d-104">Bir ifade ağacının yürütülmesi bir değer döndürebilir veya bir yöntemi çağırmak gibi yalnızca bir eylem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="fa56d-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="fa56d-105">Yalnızca Lambda ifadelerini temsil eden ifade ağaçları yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="fa56d-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="fa56d-106">Lambda ifadelerini temsil eden ifade ağaçları <xref:System.Linq.Expressions.LambdaExpression> veya <xref:System.Linq.Expressions.Expression%601>türündedir.</span><span class="sxs-lookup"><span data-stu-id="fa56d-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="fa56d-107">Bu ifade ağaçlarını yürütmek için <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> yöntemini çağırarak yürütülebilir bir temsilci oluşturun ve ardından temsilciyi çağırın.</span><span class="sxs-lookup"><span data-stu-id="fa56d-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fa56d-108">Temsilcinin türü bilinmiyorsa, diğer bir deyişle, lambda ifadesi <xref:System.Linq.Expressions.LambdaExpression> türüdür ve <xref:System.Linq.Expressions.Expression%601>değil, temsilci üzerinde <xref:System.Delegate.DynamicInvoke%2A> yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fa56d-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="fa56d-109">Bir ifade ağacı bir lambda ifadesini temsil etmez, <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemini çağırarak, gövdesi olarak özgün ifade ağacını içeren yeni bir lambda ifadesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa56d-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="fa56d-110">Ardından, bu bölümde daha önce anlatıldığı gibi lambda ifadesini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa56d-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa56d-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="fa56d-111">Example</span></span>  
 <span data-ttu-id="fa56d-112">Aşağıdaki kod örneği, bir lambda ifadesi oluşturarak ve yürüterek bir sayıyı bir üsle yükseltmeyi temsil eden bir ifade ağacının nasıl yürütüleceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fa56d-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="fa56d-113">Bu, kuvvet olarak oluşturulan sayıyı temsil eden sonuç görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="fa56d-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compile-the-code"></a><span data-ttu-id="fa56d-114">Kod derleme</span><span class="sxs-lookup"><span data-stu-id="fa56d-114">Compile the code</span></span>  
  
- <span data-ttu-id="fa56d-115">System. Linq. Ifadeler ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="fa56d-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa56d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa56d-116">See also</span></span>

- [<span data-ttu-id="fa56d-117">İfade ağaçları (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa56d-117">Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [<span data-ttu-id="fa56d-118">Nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa56d-118">How to: Modify Expression Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
