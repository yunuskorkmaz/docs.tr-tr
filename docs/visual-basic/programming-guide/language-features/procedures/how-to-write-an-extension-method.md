---
title: 'Nasıl yapılır: Uzantı Metodu Yazma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: e220a025c39757b492be033caeb8924523515804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-an-extension-method-visual-basic"></a>Nasıl yapılır: Uzantı Metodu Yazma (Visual Basic)
Genişletme yöntemleri, varolan bir sınıfa yöntemleri eklemenize olanak tanır. Bu sınıfın örneğini değilmiş gibi genişletme yöntemi çağrılabilir.  
  
### <a name="to-define-an-extension-method"></a>Bir genişletme yöntemi tanımlamak için  
  
1.  Yeni veya varolan bir Visual Basic uygulama Visual Studio'da açın.  
  
2.  Bir genişletme yöntemi tanımlamak istediğiniz dosyanın üst kısmında, aşağıdaki içeri aktarma deyimini şunlardır:  
  
    ```  
    Imports System.Runtime.CompilerServices  
    ```  
  
3.  Yeni veya var olan uygulamanızı modülde içinde uzantısı özniteliği yöntemi tanımıyla başlayın:  
  
    ```  
    <Extension()>  
    ```  
  
4.  İlk parametre türü, genişletmek istediğiniz veri türü olmalıdır dışında yönteminizi normal şekilde bildirin.  
  
    ```  
    <Extension()>   
    Public Sub subName (ByVal para1 As ExtendedType, <other parameters>)  
         ' < Body of the method >  
    End Sub  
    ```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte bir genişletme yöntemi modülünde bildirir `StringExtensions`. İkinci bir modül `Module1`, alır `StringExtensions` ve yöntemini çağırır. Bunu çağrıldığında genişletme yöntemi kapsamında olması gerekir. Genişletme yöntemi `PrintAndPunctuate` genişletir <xref:System.String> noktalama simge parametre olarak gönderilen bir dize arkasından sınıfı string örneği görüntüleyen bir yöntem.  
  
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
  
 Yöntemi iki parametre ile tanımlanan ve yalnızca biriyle adlı dikkat edin. İlk parametre `aString`, yönteminde tanımı bağlı `example`, örneğinin `String` yöntemini çağırır. Örnek çıktı aşağıdaki gibidir:  
  
 `Hello?`  
  
 `Hello!!!!`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>  
 [Genişletme Yöntemleri](./extension-methods.md)  
 [Module Deyimi](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Yordam Parametreleri ve Bağımsız Değişkenleri](./procedure-parameters-and-arguments.md)  
 [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
