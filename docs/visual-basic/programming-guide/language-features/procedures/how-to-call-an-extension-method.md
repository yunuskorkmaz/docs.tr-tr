---
title: 'Nasıl yapılır: Uzantı Metodu Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: a19705a8f90833d48869df26a18d19b0ad1488e0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340402"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Nasıl yapılır: Uzantı Metodu Çağırma (Visual Basic)

Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar. Bir uzantı yöntemi bildirilip, kapsama getirildikten sonra, onu genişlettiği türün örnek yöntemi gibi çağırabilirsiniz. Uzantı yöntemi yazma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzantı yöntemi yazma](./how-to-write-an-extension-method.md).

 Aşağıdaki yönergeler `PrintAndPunctuate`uzantı yöntemine başvurur. Bu, onu çağıran dize örneğini ve ardından ikinci parametre için ' de gönderilen değeri gösterir `punc`.

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

1. Uzantı yönteminin ilk parametresinin veri türüne sahip bir değişken bildirin. `PrintAndPunctuate`için bir <xref:System.String> değişkenine ihtiyacınız vardır:

    ```vb
    Dim example = "Ready"
    ```

2. Bu değişken, genişletme yöntemini çağırır ve değeri ilk parametreye bağlanır `aString`. Aşağıdaki çağırma ifadesinde `Ready?`görüntülenir.

    ```vb
    example.PrintAndPunctuate("?")
    ```

     Bu genişletme yöntemine yapılan çağrının, tek bir parametre gerektiren <xref:System.String> örnek metotlarından birine yapılan bir çağrı gibi göründüğünü unutmayın:

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. Başka bir dize değişkeni bildirin ve herhangi bir dizeyle çalıştığını görmek için yöntemi yeniden çağırın.

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     Sonuç şu anda: `or not!!!`.

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

- [Nasıl yapılır: Genişletme Yöntemi Yazma](./how-to-write-an-extension-method.md)
- [Genişletme Yöntemleri](./extension-methods.md)
- [Visual Basic kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
