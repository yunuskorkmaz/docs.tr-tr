---
title: 'Nasıl yapılır: Uzantı metodu yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 7a7a9d16d9f69071e9d1dacb0558f7ca92e1d21e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631026"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Nasıl yapılır: Uzantı metodu yazma (Visual Basic)
Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar. Genişletme yöntemi, bu sınıfın bir örneği gibi çağrılabilir.

### <a name="to-define-an-extension-method"></a>Bir genişletme yöntemi tanımlamak için

1. Visual Studio 'da yeni veya mevcut bir Visual Basic uygulaması açın.

2. Uzantı yöntemi tanımlamak istediğiniz dosyanın en üstünde, aşağıdaki içeri aktarma ifadesini ekleyin:

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. Yeni veya mevcut uygulamanızdaki bir modül içinde, yöntem tanımını uzantı özniteliğiyle başlatın:

    ```vb
    <Extension()>
    ```

4. Yöntemi sıradan bir şekilde bildirin, ancak ilk parametre türü genişletmek istediğiniz veri türü olmalıdır.

    ```vb
    <Extension()>
    Public Sub SubName (ByVal para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, modülünde `StringExtensions`bir genişletme yöntemi bildirir. İkinci bir modül, `Module1`yöntemini içeri `StringExtensions` aktarır ve çağırır. Uzantı yöntemi çağrıldığında kapsam içinde olmalıdır. Genişletme yöntemi `PrintAndPunctuate` , <xref:System.String> sınıfını bir parametre olarak gönderilen bir noktalama sembolleri dizesi gelen dize örneğini görüntüleyen bir yöntemle genişletir.
  
```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(ByVal aString As String,
                                 ByVal punc As String)
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
  
 Yöntemin iki parametre ile tanımlandığından ve yalnızca bir ile çağırdığına dikkat edin. Yöntem tanımındaki ilk parametre `aString`, yöntemini çağıran örneği `String` olan öğesine `example`bağlanır. Örneğin çıktısı aşağıdaki gibidir:
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Genişletme Yöntemleri](./extension-methods.md)
- [Module Deyimi](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Visual Basic kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
