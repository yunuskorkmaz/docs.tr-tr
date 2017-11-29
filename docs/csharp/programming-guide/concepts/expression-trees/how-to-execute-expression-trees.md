---
title: "Nasıl yapılır: ifade ağaçlarını (C#) yürütme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9a87c9893de2b70c47f0ed78a92adc6bce10db7b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="61be1-102">Nasıl yapılır: ifade ağaçlarını (C#) yürütme</span><span class="sxs-lookup"><span data-stu-id="61be1-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="61be1-103">Bu konuda bir ifade ağacına yürütme gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="61be1-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="61be1-104">Bir ifade ağacına yürütülürken bir değer döndürebilir ya da yalnızca bir yöntemi çağırma gibi bir eylem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="61be1-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="61be1-105">Lambda ifadeleri temsil eden ifade ağaçları çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="61be1-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="61be1-106">Lambda ifadeleri temsil ifade ağaçları türündedir <xref:System.Linq.Expressions.LambdaExpression> veya <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="61be1-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="61be1-107">Bu ifade ağaçlarını yürütme çağrısı <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> yürütülebilir bir temsilci oluşturma ve temsilci çağırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61be1-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61be1-108">Temsilci türü bilinmiyor, diğer bir deyişle, lambda ifadesi türü ise <xref:System.Linq.Expressions.LambdaExpression> ve <xref:System.Linq.Expressions.Expression%601>, çağırmalısınız <xref:System.Delegate.DynamicInvoke%2A> doğrudan çağırma yerine temsilci yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61be1-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="61be1-109">Bir ifade ağacına bir lambda ifadesi göstermiyor, özgün ifade ağacına çağırarak kendi gövdesi olarak sahip yeni bir lambda ifadesi oluşturabilirsiniz <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="61be1-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="61be1-110">Ardından, bu bölümde daha önce açıklandığı gibi lambda ifadesi yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="61be1-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61be1-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="61be1-111">Example</span></span>  
 <span data-ttu-id="61be1-112">Aşağıdaki kod örneği, bir lambda ifadesi oluşturma ve yürütme güç sayıya oluşturma işlemi temsil eden bir ifade ağacına yürütmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="61be1-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="61be1-113">Yükseltilmiş numarasını gücünü temsil eder, sonuç görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="61be1-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="61be1-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="61be1-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="61be1-115">Zaten başvurulmayan varsa System.Core.dll proje başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="61be1-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="61be1-116">System.Linq.Expressions ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="61be1-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61be1-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="61be1-117">See Also</span></span>  
 [<span data-ttu-id="61be1-118">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="61be1-118">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="61be1-119">Nasıl yapılır: ifade ağaçlarını (C#) değiştirme</span><span class="sxs-lookup"><span data-stu-id="61be1-119">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
