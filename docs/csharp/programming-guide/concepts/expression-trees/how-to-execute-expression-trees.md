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
# <a name="how-to-execute-expression-trees-c"></a>İfade ağaçlarını yürütme (C#)
Bu konu başlığı altında, bir ifade ağacının nasıl yürütüleceği gösterilmektedir. Bir ifade ağacının yürütülmesi bir değer döndürebilir veya bir yöntemi çağırmak gibi yalnızca bir eylem gerçekleştirebilir.  
  
 Yalnızca Lambda ifadelerini temsil eden ifade ağaçları yürütülebilir. Lambda ifadelerini temsil eden ifade ağaçları <xref:System.Linq.Expressions.LambdaExpression> veya türündedir <xref:System.Linq.Expressions.Expression%601> . Bu ifade ağaçlarını yürütmek için, <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> yürütülebilir bir temsilci oluşturmak üzere yöntemini çağırın ve ardından temsilciyi çağırın.  
  
> [!NOTE]
> Temsilcinin türü bilinmiyorsa, diğer bir deyişle, lambda ifadesi türündedir <xref:System.Linq.Expressions.LambdaExpression> ve değil <xref:System.Linq.Expressions.Expression%601> , <xref:System.Delegate.DynamicInvoke%2A> yöntemi doğrudan çağırmak yerine temsilci üzerinde çağırmanız gerekir.  
  
 Bir ifade ağacı bir lambda ifadesini temsil etmez, yöntemini çağırarak, gövdesi olarak özgün ifade ağacını içeren yeni bir lambda ifadesi oluşturabilirsiniz <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> . Ardından, bu bölümde daha önce anlatıldığı gibi lambda ifadesini çalıştırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir lambda ifadesi oluşturarak ve yürüterek bir sayıyı bir üsle yükseltmeyi temsil eden bir ifade ağacının nasıl yürütüleceğini göstermektedir. Bu, kuvvet olarak oluşturulan sayıyı temsil eden sonuç görüntülenir.  
  
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
  
- System. Linq. Ifadeler ad alanını ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (C#)](./index.md)
- [İfade ağaçlarını değiştirme (C#)](./how-to-modify-expression-trees.md)
