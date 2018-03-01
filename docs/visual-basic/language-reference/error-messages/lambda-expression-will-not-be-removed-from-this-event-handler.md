---
title: "Lambda ifadesi bu olay işleyiciden kaldırılmayacak"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1a4c57d1f8f41d2d9ebb645d3f2628c32a2c4e4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>Lambda ifadesi bu olay işleyiciden kaldırılmayacak
Lambda ifadesi bu olay işleyiciden kaldırılmayacak. Lambda ifadesi bir değişkene atayın ve değişkeni ekleyin ve olayı kaldırmak için kullanın.  
  
 Lambda ifadeleri olay işleyicileri ile kullanıldığında, beklediğiniz davranışı göremeyebilirsiniz. Aynı olsa derleyici her lambda ifadesi tanımı için yeni bir yöntem oluşturur. Aşağıdaki görüntüler bu nedenle, kod `False`.  
  
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
  
 Lambda ifadeleri olay işleyicileri ile kullanıldığında bu beklenmeyen sonuçlara neden olabilir. Aşağıdaki örnekte, lambda ifadesi eklenen tarafından `AddHandler` tarafından kaldırılmaz `RemoveHandler` deyimi.  
  
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
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata ele hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42326  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Uyarıyı önlemek ve lambda ifadesi kaldırmak için lambda ifadesi bir değişkene atayın ve değişkenin hem de `AddHandler` ve `RemoveHandler` aşağıdaki örnekte gösterildiği gibi deyimleri.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Olayları](../../../visual-basic/programming-guide/language-features/events/index.md)
