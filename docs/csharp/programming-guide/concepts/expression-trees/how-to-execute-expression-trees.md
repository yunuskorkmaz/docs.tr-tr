---
title: 'Nasıl yapılır: Ifade ağaçlarını yürütme (C#)'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 4a73201d06d21964a40fbbe57fa952da35c5942c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924365"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="15349-102">Nasıl yapılır: Ifade ağaçlarını yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="15349-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="15349-103">Bu konu başlığı altında, bir ifade ağacının nasıl yürütüleceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="15349-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="15349-104">Bir ifade ağacının yürütülmesi bir değer döndürebilir veya bir yöntemi çağırmak gibi yalnızca bir eylem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="15349-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="15349-105">Yalnızca Lambda ifadelerini temsil eden ifade ağaçları yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="15349-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="15349-106">Lambda ifadelerini temsil eden ifade ağaçları veya <xref:System.Linq.Expressions.LambdaExpression> <xref:System.Linq.Expressions.Expression%601>türündedir.</span><span class="sxs-lookup"><span data-stu-id="15349-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="15349-107">Bu ifade ağaçlarını yürütmek için, yürütülebilir bir <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> temsilci oluşturmak üzere yöntemini çağırın ve ardından temsilciyi çağırın.</span><span class="sxs-lookup"><span data-stu-id="15349-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15349-108">Temsilcinin türü bilinmiyorsa, diğer bir deyişle, lambda ifadesi türündedir <xref:System.Linq.Expressions.LambdaExpression> ve değil <xref:System.Linq.Expressions.Expression%601> <xref:System.Delegate.DynamicInvoke%2A> , yöntemi doğrudan çağırmak yerine temsilci üzerinde çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="15349-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="15349-109">Bir ifade ağacı bir lambda ifadesini temsil etmez, <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemini çağırarak, gövdesi olarak özgün ifade ağacını içeren yeni bir lambda ifadesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15349-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="15349-110">Ardından, bu bölümde daha önce anlatıldığı gibi lambda ifadesini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="15349-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15349-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="15349-111">Example</span></span>  
 <span data-ttu-id="15349-112">Aşağıdaki kod örneği, bir lambda ifadesi oluşturarak ve yürüterek bir sayıyı bir üsle yükseltmeyi temsil eden bir ifade ağacının nasıl yürütüleceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="15349-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="15349-113">Bu, kuvvet olarak oluşturulan sayıyı temsil eden sonuç görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="15349-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
```csharp  
// The expression tree to execute.  
BinaryExpression be = Expression.Power(Expression.Constant(2D), Expression.Constant(3D));  
  
// Create a lambda expression.  
Expression<Func<double>> le = Expression.Lambda<Func<double>>(be);  
  
// Compile the lambda expression.  
Func<double> compiledExpression = le.Compile();  
  
// Execute the lambda expression.  
double result = compiledExpression();  
  
// Display the result.  
Console.WriteLine(result);  
  
// This code produces the following output:  
// 8  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="15349-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="15349-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="15349-115">System. Linq. Ifadeler ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="15349-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15349-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="15349-116">See also</span></span>

- [<span data-ttu-id="15349-117">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="15349-117">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="15349-118">Nasıl yapılır: Ifade ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="15349-118">How to: Modify Expression Trees (C#)</span></span>](./how-to-modify-expression-trees.md)
