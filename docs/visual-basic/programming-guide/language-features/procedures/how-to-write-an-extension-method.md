---
title: 'Nasıl yapılır: Uzantı Metodu Yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 4671728330614f0f3da23fd90f5e635ddcf46578
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581151"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Nasıl yapılır: Uzantı Metodu Yazma (Visual Basic)

Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar. Genişletme yöntemi, bu sınıfın bir örneği gibi çağrılabilir.

### <a name="to-define-an-extension-method"></a>Bir genişletme yöntemi tanımlamak için

1. Visual Studio 'da yeni veya mevcut bir Visual Basic uygulaması açın.

2. Uzantı yöntemi tanımlamak istediğiniz dosyanın en üstünde, aşağıdaki içeri aktarma ifadesini ekleyin:

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. Yeni veya mevcut uygulamanızdaki bir modül içinde [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) özniteliğiyle yöntem tanımını başlatın:

    ```vb
    <Extension()>
    ```

    @No__t_0 özniteliğinin bir Visual Basic [modülünde](../../../language-reference/statements/module-statement.md)yalnızca bir yönteme (bir `Sub` veya `Function` yordamına) uygulanabileceğini unutmayın. Bunu bir `Class` veya `Structure` ' deki bir yönteme uygularsanız, Visual Basic Derleyicisi Hata [BC36551](../../../misc/bc36551.md)oluşturuyor, "uzantı yöntemleri yalnızca modüllerde tanımlanabilir."

4. Yöntemi sıradan bir şekilde bildirin, ancak ilk parametre türü genişletmek istediğiniz veri türü olmalıdır.

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>Örnek

Aşağıdaki örnek, `StringExtensions` modülünde bir genişletme yöntemi bildirir. İkinci bir modül olan `Module1`, `StringExtensions` içeri aktarır ve yöntemini çağırır. Uzantı yöntemi çağrıldığında kapsam içinde olmalıdır. Genişletme yöntemi `PrintAndPunctuate` <xref:System.String> sınıfını bir parametre olarak gönderilen bir noktalama sembolleri dizesi tarafından izlenen bir yöntem ile genişletir.

```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub

End Module
```

Yöntemin iki parametre ile tanımlandığından ve yalnızca bir ile çağırdığına dikkat edin. Yöntem tanımındaki `aString` olan ilk parametre, yöntemi çağıran `String` örneği olan `example` ' e bağlanır. Örneğin çıktısı aşağıdaki gibidir:

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Genişletme Yöntemleri](extension-methods.md)
- [Module Deyimi](../../../language-reference/statements/module-statement.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](procedure-parameters-and-arguments.md)
- [Visual Basic kapsam](../declared-elements/scope.md)
