---
title: 'Nasıl yapılır: (Visual Basic) uzantı metodu yazma'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 00d62d275f7afc06e066a375dc1ffcd74b23c9ed
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59313768"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Nasıl yapılır: (Visual Basic) uzantı metodu yazma
Genişletme yöntemleri varolan bir sınıfa yöntemler eklemenize imkan tanır. Bu sınıfın bir örneğini değilmiş gibi uzantı metodu volat pouze jednou.  
  
### <a name="to-define-an-extension-method"></a>Bir genişletme yöntemi tanımlamak için  
  
1. Yeni veya mevcut bir Visual Basic uygulamaları Visual Studio'da açın.  
  
2. Bir genişletme yöntemi tanımlamak istediğiniz dosyasının en üstüne aşağıdaki içeri aktarma deyimi içerir:  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3. İçinde bir modül, yeni veya mevcut uygulamanızda uzantı özniteliğine sahip yöntem tanımını başlayın:  
  
    ```  
    <Extension()>  
    ```  
  
4. Dışında ilk parametresinin türü genişletmek istediğiniz veri türünde olmalıdır, yöntemi normal şekilde bildirin.  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir genişletme yöntemi modülünde bildirir `StringExtensions`. İkinci bir modül `Module1`, aktarır `StringExtensions` yöntemini çağırır. Genişletme yöntemi, çağrıldığı zaman kapsamda olması gerekir. Genişletme yöntemi `PrintAndPunctuate` genişletir <xref:System.String> sınıfı dize örneğinde görüntüleyen bir yöntem ile ardından noktalama simgeleri parametre olarak gönderilen bir dize.  
  
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
  
 Yöntemi iki parametre ile tanımlanmıştır ve yalnızca bir adı olduğuna dikkat edin. İlk parametre `aString`, yöntem tanımını bağlı `example`, örneğini `String` yöntemi çağırır. Örnek çıktısı aşağıdaki gibidir:  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [Genişletme Yöntemleri](./extension-methods.md)
- [Module Deyimi](../../../../visual-basic/language-reference/statements/module-statement.md)
- [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)
- [Visual Basic'de Kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
