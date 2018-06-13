---
title: 'Nasıl yapılır: ifade ağaçlarını (C#) yürütme'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 0ebdcb603a1adf3602e897db284faa2f75b7de7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322097"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="77295-102">Nasıl yapılır: ifade ağaçlarını (C#) yürütme</span><span class="sxs-lookup"><span data-stu-id="77295-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="77295-103">Bu konuda bir ifade ağacına yürütme gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="77295-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="77295-104">Bir ifade ağacına yürütülürken bir değer döndürebilir ya da yalnızca bir yöntemi çağırma gibi bir eylem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="77295-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="77295-105">Lambda ifadeleri temsil eden ifade ağaçları çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="77295-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="77295-106">Lambda ifadeleri temsil ifade ağaçları türündedir <xref:System.Linq.Expressions.LambdaExpression> veya <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="77295-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="77295-107">Bu ifade ağaçlarını yürütme çağrısı <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> yürütülebilir bir temsilci oluşturma ve temsilci çağırma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77295-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77295-108">Temsilci türü bilinmiyor, diğer bir deyişle, lambda ifadesi türü ise <xref:System.Linq.Expressions.LambdaExpression> ve <xref:System.Linq.Expressions.Expression%601>, çağırmalısınız <xref:System.Delegate.DynamicInvoke%2A> doğrudan çağırma yerine temsilci yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77295-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="77295-109">Bir ifade ağacına bir lambda ifadesi göstermiyor, özgün ifade ağacına çağırarak kendi gövdesi olarak sahip yeni bir lambda ifadesi oluşturabilirsiniz <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77295-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="77295-110">Ardından, bu bölümde daha önce açıklandığı gibi lambda ifadesi yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="77295-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77295-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="77295-111">Example</span></span>  
 <span data-ttu-id="77295-112">Aşağıdaki kod örneği, bir lambda ifadesi oluşturma ve yürütme güç sayıya oluşturma işlemi temsil eden bir ifade ağacına yürütmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="77295-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="77295-113">Yükseltilmiş numarasını gücünü temsil eder, sonuç görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="77295-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="77295-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="77295-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="77295-115">Zaten başvurulmayan varsa System.Core.dll proje başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="77295-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="77295-116">System.Linq.Expressions ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="77295-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77295-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77295-117">See Also</span></span>  
 [<span data-ttu-id="77295-118">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="77295-118">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
 [<span data-ttu-id="77295-119">Nasıl yapılır: ifade ağaçlarını (C#) değiştirme</span><span class="sxs-lookup"><span data-stu-id="77295-119">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
