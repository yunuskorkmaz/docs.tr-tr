---
title: 'Nasıl yapılır: ifade ağaçlarını (C#) yürütme'
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: 2aad970946e417d623907c9f832e2c6e29eef912
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560776"
---
# <a name="how-to-execute-expression-trees-c"></a>Nasıl yapılır: ifade ağaçlarını (C#) yürütme
Bu konu nasıl bir ifade ağacı çalıştırılacağını gösterir. İfade ağacı yürütülürken bir değer döndürebilir veya sadece bir yöntemi gibi bir eylem gerçekleştirebilir.  
  
 Lambda ifadeleri temsil eden ifade ağaçları çalıştırılabilir. Lambda ifadeleri temsil eden ifade ağaçları, tür <xref:System.Linq.Expressions.LambdaExpression> veya <xref:System.Linq.Expressions.Expression%601>. Bu ifade ağaçlarını yürütme için çağrı <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> yürütülebilir bir temsilci oluşturmak ve ardından temsilci çağırmak için yöntem.  
  
> [!NOTE]
>  Metot temsilcisinin türü bilinmiyor, diğer bir deyişle, lambda ifadesi türü ise <xref:System.Linq.Expressions.LambdaExpression> değil <xref:System.Linq.Expressions.Expression%601>, çağırmalısınız <xref:System.Delegate.DynamicInvoke%2A> yöntemini doğrudan çağırmak yerine temsilci.  
  
 Bir lambda ifadesi ifade ağacına temsil etmiyorsa çağırarak orijinal ifade ağacı, gövdeye, sahip yeni bir lambda ifadesi oluşturabilirsiniz <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemi. Ardından, lambda ifadesi bu bölümde daha önce açıklanan şekilde yürütebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir lambda ifadesi oluşturma ve yürütme güç bir sayıya yükseltme temsil eden bir ifade ağacı yürütülecek gösterilmiştir. Oluşturulan sayı gücünü temsil eder, sonuç görüntülenir.  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   Zaten başvurulmayan System.Core.dll bir proje başvurusu ekleyin.  
  
-   System.Linq.Expressions ad alanı içerir.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [İfade ağaçları (C#)](../../../../csharp/programming-guide/concepts/expression-trees/index.md)  
- [Nasıl yapılır: ifade ağaçlarını (C#) değiştirme](../../../../csharp/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
