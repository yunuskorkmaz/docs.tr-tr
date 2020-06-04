---
title: 'Nasıl yapılır: Uzantı Yöntemi Çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 54419c99ae08c9ca2e3cfa86993dc99bc02bbb64
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388666"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Nasıl yapılır: Uzantı Metodu Çağırma (Visual Basic)

Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar. Bir uzantı yöntemi bildirilip, kapsama getirildikten sonra, onu genişlettiği türün örnek yöntemi gibi çağırabilirsiniz. Uzantı yöntemi yazma hakkında daha fazla bilgi için bkz. [nasıl yapılır: uzantı yöntemi yazma](./how-to-write-an-extension-method.md).

 Aşağıdaki yönergeler, `PrintAndPunctuate` onu çağıran dize örneğini görüntüleyen ve ikinci parametresi için ' de gönderilen değer tarafından izlenen uzantı yöntemini ifade eder `punc` .

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

1. Uzantı yönteminin ilk parametresinin veri türüne sahip bir değişken bildirin. İçin `PrintAndPunctuate` bir değişkene ihtiyacınız vardır <xref:System.String> :

    ```vb
    Dim example = "Ready"
    ```

2. Bu değişken, genişletme yöntemini çağıracaktır ve değeri ilk parametreye bağlanır `aString` . Aşağıdaki çağırma deyimleri görüntülenecektir `Ready?` .

    ```vb
    example.PrintAndPunctuate("?")
    ```

     Bu uzantı yöntemine yapılan çağrının, <xref:System.String> tek bir parametre gerektiren örnek metotlarından herhangi birine bir çağrı gibi göründüğünü unutmayın:

    ```vb
    example.EndsWith("dy")
    example.IndexOf("R")
    ```

3. Başka bir dize değişkeni bildirin ve herhangi bir dizeyle çalıştığını görmek için yöntemi yeniden çağırın.

    ```vb
    Dim example2 = " or not"
    example2.PrintAndPunctuate("!!!")
    ```

     Sonuç bu zaman: `or not!!!` .

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
- [Uzantı yöntemleri](./extension-methods.md)
- [Visual Basic'de Kapsam](../declared-elements/scope.md)
