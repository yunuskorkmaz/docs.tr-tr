---
title: 'Nasıl yapılır: ifade ağaçlarını (C#) yürütme'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 2aad970946e417d623907c9f832e2c6e29eef912
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192528"
---
# <a name="how-to-execute-expression-trees-c"></a><span data-ttu-id="ebeba-102">Nasıl yapılır: ifade ağaçlarını (C#) yürütme</span><span class="sxs-lookup"><span data-stu-id="ebeba-102">How to: Execute Expression Trees (C#)</span></span>
<span data-ttu-id="ebeba-103">Bu konu nasıl bir ifade ağacı çalıştırılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ebeba-103">This topic shows you how to execute an expression tree.</span></span> <span data-ttu-id="ebeba-104">İfade ağacı yürütülürken bir değer döndürebilir veya sadece bir yöntemi gibi bir eylem gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="ebeba-104">Executing an expression tree may return a value, or it may just perform an action such as calling a method.</span></span>  
  
 <span data-ttu-id="ebeba-105">Lambda ifadeleri temsil eden ifade ağaçları çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="ebeba-105">Only expression trees that represent lambda expressions can be executed.</span></span> <span data-ttu-id="ebeba-106">Lambda ifadeleri temsil eden ifade ağaçları, tür <xref:System.Linq.Expressions.LambdaExpression> veya <xref:System.Linq.Expressions.Expression%601>.</span><span class="sxs-lookup"><span data-stu-id="ebeba-106">Expression trees that represent lambda expressions are of type <xref:System.Linq.Expressions.LambdaExpression> or <xref:System.Linq.Expressions.Expression%601>.</span></span> <span data-ttu-id="ebeba-107">Bu ifade ağaçlarını yürütme için çağrı <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> yürütülebilir bir temsilci oluşturmak ve ardından temsilci çağırmak için yöntem.</span><span class="sxs-lookup"><span data-stu-id="ebeba-107">To execute these expression trees, call the <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> method to create an executable delegate, and then invoke the delegate.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebeba-108">Metot temsilcisinin türü bilinmiyor, diğer bir deyişle, lambda ifadesi türü ise <xref:System.Linq.Expressions.LambdaExpression> değil <xref:System.Linq.Expressions.Expression%601>, çağırmalısınız <xref:System.Delegate.DynamicInvoke%2A> yöntemini doğrudan çağırmak yerine temsilci.</span><span class="sxs-lookup"><span data-stu-id="ebeba-108">If the type of the delegate is not known, that is, the lambda expression is of type <xref:System.Linq.Expressions.LambdaExpression> and not <xref:System.Linq.Expressions.Expression%601>, you must call the <xref:System.Delegate.DynamicInvoke%2A> method on the delegate instead of invoking it directly.</span></span>  
  
 <span data-ttu-id="ebeba-109">Bir lambda ifadesi ifade ağacına temsil etmiyorsa çağırarak orijinal ifade ağacı, gövdeye, sahip yeni bir lambda ifadesi oluşturabilirsiniz <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ebeba-109">If an expression tree does not represent a lambda expression, you can create a new lambda expression that has the original expression tree as its body, by calling the <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> method.</span></span> <span data-ttu-id="ebeba-110">Ardından, lambda ifadesi bu bölümde daha önce açıklanan şekilde yürütebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebeba-110">Then, you can execute the lambda expression as described earlier in this section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebeba-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="ebeba-111">Example</span></span>  
 <span data-ttu-id="ebeba-112">Aşağıdaki kod örneği, bir lambda ifadesi oluşturma ve yürütme güç bir sayıya yükseltme temsil eden bir ifade ağacı yürütülecek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ebeba-112">The following code example demonstrates how to execute an expression tree that represents raising a number to a power by creating a lambda expression and executing it.</span></span> <span data-ttu-id="ebeba-113">Oluşturulan sayı gücünü temsil eder, sonuç görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ebeba-113">The result, which represents the number raised to the power, is displayed.</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ebeba-114">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ebeba-114">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ebeba-115">Zaten başvurulmayan System.Core.dll bir proje başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="ebeba-115">Add a project reference to System.Core.dll if it is not already referenced.</span></span>  
  
-   <span data-ttu-id="ebeba-116">System.Linq.Expressions ad alanı içerir.</span><span class="sxs-lookup"><span data-stu-id="ebeba-116">Include the System.Linq.Expressions namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebeba-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ebeba-117">See Also</span></span>

- [<span data-ttu-id="ebeba-118">İfade ağaçları (C#)</span><span class="sxs-lookup"><span data-stu-id="ebeba-118">Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
- [<span data-ttu-id="ebeba-119">Nasıl yapılır: ifade ağaçlarını (C#) değiştirme</span><span class="sxs-lookup"><span data-stu-id="ebeba-119">How to: Modify Expression Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
