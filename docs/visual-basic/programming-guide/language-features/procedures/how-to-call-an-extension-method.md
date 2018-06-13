---
title: 'Nasıl yapılır: Uzantı Metodu Çağırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 32691183bcd1632a82b1e9a2668790abbf8f80fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648573"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Nasıl yapılır: Uzantı Metodu Çağırma (Visual Basic)
Genişletme yöntemleri, varolan bir sınıfa yöntemleri eklemenize olanak tanır. Bir genişletme yöntemi bildirilen ve kapsam içine alındıktan sonra onu genişleyen türü gibi bir örnek yöntemi çağırabilirsiniz. Uzantı metodu yazma hakkında daha fazla bilgi için bkz: [nasıl yapılır: uzantı yöntemi yazma](./how-to-write-an-extension-method.md).  
  
 Genişletme yöntemi aşağıdaki yönergelere bakın `PrintAndPunctuate`, hangi, ne olursa olsun değer tarafından izlenen çağırır string örneği görüntüler için ikinci parametresi, gönderildiği `punc`.  
  
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
  
 Bunu çağrıldığında yöntemi kapsamında olması gerekir.  
  
### <a name="to-call-an-extension-method"></a>Bir genişletme yöntemi çağırmak için  
  
1.  Uzantı yönteminin ilk parametresinin veri türüne sahip bir değişken bildirin. İçin `PrintAndPunctuate`, gereksinim duyduğunuz bir <xref:System.String> değişkeni:  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  Değişkeni genişletme yöntemi çağırmak ve değeri ilk parametre olarak bağlanmıştır `aString`. Aşağıdaki arama deyimini görüntüler `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Bu uzantı yöntem çağrısı yalnızca görünen bildirim ister herhangi biri için bir çağrı <xref:System.String> örnek bir parametre gerekli yöntemleri:  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  Başka bir dize değişkeni bildirme ve yeniden ile herhangi bir dize çalıştığını görmek için yöntemi çağırın.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Bu süre sonucudur: `or not!!!`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tam bir örnek oluşturma ve basit genişletme yöntemi kullanımını ' dir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Genişletme Yöntemi Yazma](./how-to-write-an-extension-method.md)  
 [Genişletme Yöntemleri](./extension-methods.md)  
 [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
