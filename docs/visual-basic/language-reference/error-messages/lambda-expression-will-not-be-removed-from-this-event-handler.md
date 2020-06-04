---
title: Lambda ifadesi bu olay işleyiciden kaldırılmayacak
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 07ace3f1b9c5e512227dc1f718ef768b631c8303
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397382"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>Lambda ifadesi bu olay işleyiciden kaldırılmayacak

Lambda ifadesi bu olay işleyicisinden kaldırılmayacak. Lambda ifadesini bir değişkene atayın ve olayı eklemek ve kaldırmak için değişkeni kullanın.

Lambda ifadeleri olay işleyicileriyle kullanıldığında, bekleeceğiniz davranışı göremeyebilirsiniz. Derleyici, aynı olsalar bile her bir lambda ifadesi tanımı için yeni bir yöntem oluşturur. Bu nedenle, aşağıdaki kod görüntülenir `False` .

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

Lambda ifadeleri olay işleyicileriyle kullanıldığında, bu beklenmeyen sonuçlara neden olabilir. Aşağıdaki örnekte, tarafından eklenen lambda ifadesi `AddHandler` deyimi tarafından kaldırılmaz `RemoveHandler` .

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

Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak işleme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).

**Hata kimliği:** BC42326

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Uyarıyı önlemek ve lambda ifadesini kaldırmak için lambda ifadesini bir değişkene atayın ve `AddHandler` `RemoveHandler` Aşağıdaki örnekte gösterildiği gibi değişkeni hem hem de deyimlerde kullanın.

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

- [Lambda Ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [Gevşek Temsilci Dönüştürme](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Olaylar](../../programming-guide/language-features/events/index.md)
