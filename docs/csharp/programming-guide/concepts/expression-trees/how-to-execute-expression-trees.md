---
title: İfade ağaçlarını yürütme (C#)
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: e7d408ea154572dc8b45d2e67bca3f05837868d2
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969890"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="8686a-102">İfade ağaçlarını yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="8686a-102">How to execute expression trees (C#)</span></span>
<span data-ttu-id="8686a-103">Bu konu başlığı altında, bir ifade ağacının nasıl yürütüleceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8686a-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="8686a-104">Bir ifade ağacının yürütülmesi bir değer döndürebilir veya bir yöntemi çağırmak gibi yalnızca bir eylem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="8686a-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="8686a-105">Yalnızca Lambda ifadelerini temsil eden ifade ağaçları yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="8686a-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="8686a-106">Lambda ifadelerini temsil eden ifade ağaçları <xref:System.Linq.Expressions.LambdaExpression> veya <xref:System.Linq.Expressions.Expression%601>türündedir.</span><span class="sxs-lookup"><span data-stu-id="8686a-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="8686a-107">Bu ifade ağaçlarını yürütmek için <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> yöntemini çağırarak yürütülebilir bir temsilci oluşturun ve ardından temsilciyi çağırın.</span><span class="sxs-lookup"><span data-stu-id="8686a-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8686a-108">Temsilcinin türü bilinmiyorsa, diğer bir deyişle, lambda ifadesi <xref:System.Linq.Expressions.LambdaExpression> türüdür ve <xref:System.Linq.Expressions.Expression%601>değil, temsilci üzerinde <xref:System.Delegate.DynamicInvoke%2A> yöntemini çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8686a-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="8686a-109">Bir ifade ağacı bir lambda ifadesini temsil etmez, <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemini çağırarak, gövdesi olarak özgün ifade ağacını içeren yeni bir lambda ifadesi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8686a-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="8686a-110">Ardından, bu bölümde daha önce anlatıldığı gibi lambda ifadesini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8686a-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8686a-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="8686a-111">Example</span></span>  
 <span data-ttu-id="8686a-112">Aşağıdaki kod örneği, bir lambda ifadesi oluşturarak ve yürüterek bir sayıyı bir üsle yükseltmeyi temsil eden bir ifade ağacının nasıl yürütüleceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="8686a-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="8686a-113">Bu, kuvvet olarak oluşturulan sayıyı temsil eden sonuç görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="8686a-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="8686a-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="8686a-114">Compiling the Code</span></span>  
  
- <span data-ttu-id="8686a-115">System. Linq. Ifadeler ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8686a-115">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8686a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8686a-116">See also</span></span>

- [<span data-ttu-id="8686a-117">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="8686a-117">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="8686a-118">İfade ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="8686a-118">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
