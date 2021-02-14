---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: uzantı yöntemi yazma (Visual Basic)'
title: 'Nasıl yapılır: Uzantı Metodu Yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 4c5d88976e55288ccb350ab82d459db0a23f468e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476195"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Nasıl yapılır: Uzantı Metodu Yazma (Visual Basic)

Uzantı yöntemleri varolan bir sınıfa Yöntemler eklemenizi sağlar. Genişletme yöntemi, bu sınıfın bir örneği gibi çağrılabilir.

### <a name="to-define-an-extension-method"></a>Bir genişletme yöntemi tanımlamak için

1. Visual Studio 'da yeni veya mevcut bir Visual Basic uygulaması açın.

2. Uzantı yöntemi tanımlamak istediğiniz dosyanın en üstünde, aşağıdaki içeri aktarma ifadesini ekleyin:

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. Yeni veya mevcut uygulamanızdaki bir modül içinde, yöntem tanımını [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) özniteliğiyle başlatın:

    ```vb
    <Extension()>
    ```

    `Extension`Özniteliğinin yalnızca bir Visual Basic modülündeki bir yönteme ( `Sub` veya `Function` yordama) uygulanabileceğini unutmayın. [](../../../language-reference/statements/module-statement.md) Bunu bir veya a içindeki bir yönteme uygularsanız, `Class` `Structure` Visual Basic Derleyicisi Hata [BC36551](../../../misc/bc36551.md)oluşturuyor, "uzantı yöntemleri yalnızca modüllerde tanımlanabilir."

4. Yöntemi sıradan bir şekilde bildirin, ancak ilk parametre türü genişletmek istediğiniz veri türü olmalıdır.

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a>Örnek

Aşağıdaki örnek, modülünde bir genişletme yöntemi bildirir `StringExtensions` . İkinci bir modül, `Module1` yöntemini içeri aktarır `StringExtensions` ve çağırır. Uzantı yöntemi çağrıldığında kapsam içinde olmalıdır. Genişletme yöntemi `PrintAndPunctuate` , <xref:System.String> sınıfını bir parametre olarak gönderilen bir noktalama sembolleri dizesi gelen dize örneğini görüntüleyen bir yöntemle genişletir.

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

Yöntemin iki parametre ile tanımlandığından ve yalnızca bir ile çağırdığına dikkat edin. Yöntem tanımındaki ilk parametre, `aString` `example` `String` yöntemini çağıran örneği olan öğesine bağlanır. Örneğin çıktısı aşağıdaki gibidir:

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Uzantı Metotları](extension-methods.md)
- [Module Deyimi](../../../language-reference/statements/module-statement.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](procedure-parameters-and-arguments.md)
- [Visual Basic'de Kapsam](../declared-elements/scope.md)
