---
title: 'Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 135c295070ea591f3b494734f9d236e36b9c3c5d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916495"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a>Nasıl yapılır: Ifade ağaçlarını yürütme (Visual Basic)
Bu konu başlığı altında, bir ifade ağacının nasıl yürütüleceği gösterilmektedir. Bir ifade ağacının yürütülmesi bir değer döndürebilir veya bir yöntemi çağırmak gibi yalnızca bir eylem gerçekleştirebilir.  
  
 Yalnızca Lambda ifadelerini temsil eden ifade ağaçları yürütülebilir. Lambda ifadelerini temsil eden ifade ağaçları veya <xref:System.Linq.Expressions.LambdaExpression> <xref:System.Linq.Expressions.Expression%601>türündedir. Bu ifade ağaçlarını yürütmek için, yürütülebilir bir <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> temsilci oluşturmak üzere yöntemini çağırın ve ardından temsilciyi çağırın.  
  
> [!NOTE]
> Temsilcinin türü bilinmiyorsa, diğer bir deyişle, lambda ifadesi türündedir <xref:System.Linq.Expressions.LambdaExpression> ve değil <xref:System.Linq.Expressions.Expression%601> <xref:System.Delegate.DynamicInvoke%2A> , yöntemi doğrudan çağırmak yerine temsilci üzerinde çağırmanız gerekir.  
  
 Bir ifade ağacı bir lambda ifadesini temsil etmez, <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemini çağırarak, gövdesi olarak özgün ifade ağacını içeren yeni bir lambda ifadesi oluşturabilirsiniz. Ardından, bu bölümde daha önce anlatıldığı gibi lambda ifadesini çalıştırabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir lambda ifadesi oluşturarak ve yürüterek bir sayıyı bir üsle yükseltmeyi temsil eden bir ifade ağacının nasıl yürütüleceğini göstermektedir. Bu, kuvvet olarak oluşturulan sayıyı temsil eden sonuç görüntülenir.  
  
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
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
- System. Linq. Ifadeler ad alanını ekleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Nasıl yapılır: Ifade ağaçlarını değiştirme (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
