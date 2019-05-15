---
title: 'Nasıl yapılır: (Visual Basic) ifade ağaçlarını yürütme'
ms.date: 07/20/2015
ms.assetid: 9dfb5ab3-f48f-417e-975f-f8f6f1cdc18d
ms.openlocfilehash: 62d3febf7090c6662e5593bbaf94c04236a162e9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592145"
---
# <a name="how-to-execute-expression-trees-visual-basic"></a>Nasıl yapılır: (Visual Basic) ifade ağaçlarını yürütme
Bu konu nasıl bir ifade ağacı çalıştırılacağını gösterir. İfade ağacı yürütülürken bir değer döndürebilir veya sadece bir yöntemi gibi bir eylem gerçekleştirebilir.  
  
 Lambda ifadeleri temsil eden ifade ağaçları çalıştırılabilir. Lambda ifadeleri temsil eden ifade ağaçları, tür <xref:System.Linq.Expressions.LambdaExpression> veya <xref:System.Linq.Expressions.Expression%601>. Bu ifade ağaçlarını yürütme için çağrı <xref:System.Linq.Expressions.LambdaExpression.Compile%2A> yürütülebilir bir temsilci oluşturmak ve ardından temsilci çağırmak için yöntem.  
  
> [!NOTE]
>  Metot temsilcisinin türü bilinmiyor, diğer bir deyişle, lambda ifadesi türü ise <xref:System.Linq.Expressions.LambdaExpression> değil <xref:System.Linq.Expressions.Expression%601>, çağırmalısınız <xref:System.Delegate.DynamicInvoke%2A> yöntemini doğrudan çağırmak yerine temsilci.  
  
 Bir lambda ifadesi ifade ağacına temsil etmiyorsa çağırarak orijinal ifade ağacı, gövdeye, sahip yeni bir lambda ifadesi oluşturabilirsiniz <xref:System.Linq.Expressions.Expression.Lambda%60%601%28System.Linq.Expressions.Expression%2CSystem.Collections.Generic.IEnumerable%7BSystem.Linq.Expressions.ParameterExpression%7D%29> yöntemi. Ardından, lambda ifadesi bu bölümde daha önce açıklanan şekilde yürütebilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir lambda ifadesi oluşturma ve yürütme güç bir sayıya yükseltme temsil eden bir ifade ağacı yürütülecek gösterilmiştir. Oluşturulan sayı gücünü temsil eder, sonuç görüntülenir.  
  
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
  
- System.Linq.Expressions ad alanı içerir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfade ağaçları (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Nasıl yapılır: (Visual Basic) ifade ağaçlarını değiştirme](../../../../visual-basic/programming-guide/concepts/expression-trees/how-to-modify-expression-trees.md)
