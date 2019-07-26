---
title: 'Nasıl yapılır: Bir genişletme yöntemi çağırın (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: f2058162ab939d2619d7255c884d88c35ee63715
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512669"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Nasıl yapılır: Bir genişletme yöntemi çağırın (Visual Basic)

Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar. Bir uzantı yöntemi bildirilip, kapsama getirildikten sonra, onu genişlettiği türün örnek yöntemi gibi çağırabilirsiniz. Uzantı yöntemi yazma hakkında daha fazla bilgi için bkz [. nasıl yapılır: Bir genişletme yöntemi](./how-to-write-an-extension-method.md)yazın.

 Aşağıdaki yönergeler, onu çağıran dize örneğini `PrintAndPunctuate`görüntüleyen ve ikinci `punc`parametresi için ' de gönderilen değer tarafından izlenen uzantı yöntemini ifade eder.

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

Yöntem çağrıldığında kapsam içinde olmalıdır.

### <a name="to-call-an-extension-method"></a>Bir genişletme yöntemini çağırmak için

1. Uzantı yönteminin ilk parametresinin veri türüne sahip bir değişken bildirin. İçin `PrintAndPunctuate` bir<xref:System.String> değişkene ihtiyacınız vardır:

    ```vb
    Dim example = "Ready"
    ```

2. Bu değişken, genişletme yöntemini çağıracaktır ve değeri ilk parametreye `aString`bağlanır. Aşağıdaki çağırma deyimleri görüntülenecektir `Ready?`.

    ```vb
    example.PrintAndPunctuate("?")
    ```

     Bu uzantı yöntemine yapılan çağrının, tek bir parametre gerektiren <xref:System.String> örnek metotlarından herhangi birine bir çağrı gibi göründüğünü unutmayın:

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. Başka bir dize değişkeni bildirin ve herhangi bir dizeyle çalıştığını görmek için yöntemi yeniden çağırın.

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     Sonuç bu zaman: `or not!!!`.

## <a name="example"></a>Örnek
 Aşağıdaki kod, basit bir genişletme yönteminin oluşturulması ve kullanılması için bir örnektir.

```vb
Imports System.Runtime.CompilerServices
Imports ConsoleApplication1.StringExtensions

Module Module1

    Sub Main()

        Dim example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")

        Dim example2 = "Goodbye"
        example2.PrintAndPunctuate("?")
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module

' Output:
' Hello.
' Hello!!!!
' Goodbye?
```

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Uzantı yöntemi yazma](./how-to-write-an-extension-method.md)
- [Genişletme Yöntemleri](./extension-methods.md)
- [Visual Basic kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
