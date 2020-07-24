---
title: İfade ağaçlarını yürütme (C#)
description: Bir değer döndürmek veya bir yöntemi çağırmak gibi bir eylem gerçekleştirmek için bir ifade ağacının nasıl yürütüleceğini öğrenin.
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 9e306da545ba6c6275f36b8f6dd4e98bb91ed54e
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105614"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="d83f4-103">İfade ağaçlarını yürütme (C#)</span><span class="sxs-lookup"><span data-stu-id="d83f4-103">How to execute expression trees (C#)</span></span>
<span data-ttu-id="d83f4-104">Bu konu başlığı altında, bir ifade ağacının nasıl yürütüleceği gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d83f4-104">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="d83f4-105">Bir ifade ağacının yürütülmesi bir değer döndürebilir veya bir yöntemi çağırmak gibi yalnızca bir eylem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d83f4-105">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="d83f4-106">Yalnızca Lambda ifadelerini temsil eden ifade ağaçları yürütülebilir.</span><span class="sxs-lookup"><span data-stu-id="d83f4-106">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="d83f4-107">Lambda ifadelerini temsil eden ifade ağaçları <xref:System.Linq.Expressions.LambdaExpression> veya türündedir <xref:System.Linq.Expressions.Expression%601> .</span><span class="sxs-lookup"><span data-stu-id="d83f4-107">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="d83f4-108">Bu ifade ağaçlarını yürütmek için, <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> yürütülebilir bir temsilci oluşturmak üzere yöntemini çağırın ve ardından temsilciyi çağırın.</span><span class="sxs-lookup"><span data-stu-id="d83f4-108">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d83f4-109">Temsilcinin türü bilinmiyorsa, diğer bir deyişle, lambda ifadesi türündedir <xref:System.Linq.Expressions.LambdaExpression> ve değil <xref:System.Linq.Expressions.Expression%601> , <xref:System.Delegate.DynamicInvoke%2A> yöntemi doğrudan çağırmak yerine temsilci üzerinde çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d83f4-109">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="d83f4-110">Bir ifade ağacı bir lambda ifadesini temsil etmez, yöntemini çağırarak, gövdesi olarak özgün ifade ağacını içeren yeni bir lambda ifadesi oluşturabilirsiniz <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> .</span><span class="sxs-lookup"><span data-stu-id="d83f4-110">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="d83f4-111">Ardından, bu bölümde daha önce anlatıldığı gibi lambda ifadesini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d83f4-111">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d83f4-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="d83f4-112">Example</span></span>  
 <span data-ttu-id="d83f4-113">Aşağıdaki kod örneği, bir lambda ifadesi oluşturarak ve yürüterek bir sayıyı bir üsle yükseltmeyi temsil eden bir ifade ağacının nasıl yürütüleceğini göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="d83f4-113">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="d83f4-114">Bu, kuvvet olarak oluşturulan sayıyı temsil eden sonuç görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d83f4-114">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="d83f4-115">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d83f4-115">Compiling the Code</span></span>  
  
- <span data-ttu-id="d83f4-116">System. Linq. Ifadeler ad alanını ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d83f4-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d83f4-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d83f4-117">See also</span></span>

- [<span data-ttu-id="d83f4-118">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="d83f4-118">Expression Trees (C#)</span></span>](./index.md)
- [<span data-ttu-id="d83f4-119">İfade ağaçlarını değiştirme (C#)</span><span class="sxs-lookup"><span data-stu-id="d83f4-119">How to modify expression trees (C#)</span></span>](./how-to-modify-expression-trees.md)
