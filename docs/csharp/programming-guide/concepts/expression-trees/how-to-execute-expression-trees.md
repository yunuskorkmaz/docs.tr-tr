---
title: İfade ağaçları nasıl yürütülür (C#)
ms.date: 07/20/2015
ms.assetid: b8c40db5-2464-4bb9-9001-8c2bc7f006c5
ms.openlocfilehash: e7d408ea154572dc8b45d2e67bca3f05837868d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73969890"
---
# <a name="how-to-execute-expression-trees-c"></a>İfade ağaçları nasıl yürütülür (C#)
Bu konu, bir ifade ağacını nasıl yürütültüregösterdiğinizi gösterir. Bir ifade ağacının yürütülmesi bir değer döndürebilir veya yöntem çağırmak gibi bir eylem gerçekleştirebilir.  
  
 Yalnızca lambda ifadelerini temsil eden ifade ağaçları yürütülebilir. Lambda ifadelerini temsil eden ifade <xref:System.Linq.Expressions.LambdaExpression> <xref:System.Linq.Expressions.Expression%601>ağaçları türü veya . Bu ifade ağaçlarını yürütmek <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> için, çalıştırılabilir bir temsilci oluşturmak için yöntemi çağırın ve ardından temsilciyi çağırın.  
  
> [!NOTE]
> Temsilcinin türü bilinmiyorsa, yani lambda ifadesi türündedir <xref:System.Linq.Expressions.LambdaExpression> ve <xref:System.Linq.Expressions.Expression%601>değil, yöntemi <xref:System.Delegate.DynamicInvoke%2A> doğrudan çağırmak yerine temsilciye çağırmalısınız.  
  
 Bir ifade ağacı lambda ifadesini temsil etmiyorsa, <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemi çağırarak özgün ifade ağacını gövdesi olarak içeren yeni bir lambda ifadesi oluşturabilirsiniz. Daha sonra, bu bölümde daha önce açıklandığı gibi lambda ifadesini çalıştırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir lambda ifadesi oluşturup yürüterek bir sayıyı bir güce yükseltmeyi temsil eden bir ifade ağacının nasıl yürütüleceklerini gösterir. Güce yükseltilen sayıyı temsil eden sonuç görüntülenir.  
  
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
  
- System.Linq.Expressions ad alanını ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade Ağaçları (C#)](./index.md)
- [İfade ağaçları nasıl değiştirilir (C#)](./how-to-modify-expression-trees.md)
