---
title: Lambda ifadesi bu olay işleyiciden kaldırılmayacak
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 20e83306925e91e579aca52f2e7c209c8c686dee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817621"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>Lambda ifadesi bu olay işleyiciden kaldırılmayacak
Lambda ifadesi bu olay işleyiciden kaldırılmayacak. Lambda ifadesi bir değişkene atayın ve ekleme ve kaldırma olay için değişkeni kullanın.  
  
 Lambda ifadelerini olay işleyicileri ile kullanıldığında, beklediğiniz davranışı göremeyebilirsiniz. Aynı olsa, derleyici her bir lambda ifadesi tanımı için yeni bir yöntem oluşturur. Aşağıdaki görüntüler bu nedenle, kod `False`.  
  
```vb  
Module Module1  
  
    Sub Main()  
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1  
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1  
        Console.WriteLine(fun1 = fun2)  
    End Sub  
  
    Delegate Function ChangeInteger(ByVal x As Integer) As Integer  
  
End Module  
```  
  
 Lambda ifadelerini olay işleyicileri ile kullanıldığında, bu durum beklenmeyen sonuçlara neden olabilir. Aşağıdaki örnekte, lambda ifadesi tarafından eklenen `AddHandler` tarafından kaldırılmaz `RemoveHandler` deyimi.  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Sub Main()  
  
        ' The following line adds one listener to the event.  
        AddHandler ProcessInteger, Function(m As Integer) m  
  
        ' The following statement searches the current listeners   
        ' for a match to remove. However, this lambda is not the same  
        ' as the previous one, so nothing is removed.  
        RemoveHandler ProcessInteger, Function(m As Integer) m  
  
    End Sub  
End Module  
```  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları Gizle veya uyarıları hata olarak değerlendir hakkında daha fazla bilgi için bkz. [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42326  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Uyarıyı önlemek ve lambda ifadesindeki kaldırmak için lambda ifadesi bir değişkene atayın ve değişkenin hem de `AddHandler` ve `RemoveHandler` ifadeleri, aşağıdaki örnekte gösterildiği gibi.  
  
```vb  
Module Module1  
  
    Event ProcessInteger(ByVal x As Integer)  
  
    Dim PrintHandler As ProcessIntegerEventHandler  
  
    Sub Main()  
  
        ' Assign the lambda expression to a variable.  
        PrintHandler = Function(m As Integer) m  
  
        ' Use the variable to add the listener.  
        AddHandler ProcessInteger, PrintHandler  
  
        ' Use the variable again when you want to remove the listener.  
        RemoveHandler ProcessInteger, PrintHandler  
  
    End Sub  
End Module  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
