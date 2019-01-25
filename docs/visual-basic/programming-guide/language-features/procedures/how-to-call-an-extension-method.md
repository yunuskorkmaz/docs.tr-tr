---
title: 'Nasıl yapılır: (Visual Basic) uzantı metodu çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
ms.openlocfilehash: 4e9391a4c4a159cd5e198689bf7af7cd64c3a872
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620454"
---
# <a name="how-to-call-an-extension-method-visual-basic"></a>Nasıl yapılır: (Visual Basic) uzantı metodu çağırma
Genişletme yöntemleri varolan bir sınıfa yöntemler eklemenize imkan tanır. Bir genişletme yöntemi bildirildi ve kapsama alınır sonra bunu genişleten türü gibi bir örnek yöntemi çağırabilirsiniz. Uzantı metodu yazma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Uzantı metodu yazma](./how-to-write-an-extension-method.md).  
  
 Genişletme yöntemi için aşağıdaki yönergelere bakın `PrintAndPunctuate`, hangi değere göre ve ardından onu çağıran dize örneğinde görüntüler, ikinci parametresi, gönderildiği `punc`.  
  
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
  
 Çağrıldığında, yöntemi kapsam içinde olması gerekir.  
  
### <a name="to-call-an-extension-method"></a>Bir uzantı yöntemini çağırmak için  
  
1.  Genişletme yönteminin ilk parametresi için veri türüne sahip bir değişken bildirir. İçin `PrintAndPunctuate`, gereksinim duyduğunuz bir <xref:System.String> değişkeni:  
  
    ```  
    Dim example = "Ready"  
    ```  
  
2.  Değişkeni genişletme yöntemini çağırmak ve değeri ilk parametre olarak bağlı `aString`. Aşağıdaki deyim çağırma görüntüler `Ready?`.  
  
    ```  
    example.PrintAndPunctuate("?")  
    ```  
  
     Bu uzantı yöntemine çağrı yalnızca görünen bildirim ister bir çağrı herhangi birine <xref:System.String> örneği bir parametre gerektiren yöntemleri:  
  
    ```  
    example.EndsWith("dy")  
    example.IndexOf("R")  
    ```  
  
3.  Başka bir dize değişkeni bildirme ve yeniden herhangi bir dize ile çalışır durumda olduğunu görmek için yöntemi çağırın.  
  
    ```  
    Dim example2 = " or not"  
    example2.PrintAndPunctuate("!!!")  
    ```  
  
     Bu süre sonucudur: `or not!!!`.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, tam bir örnek oluşturma ve basit bir uzantı yönteminin kullanılmasını ' dir.  
  
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
- [Nasıl yapılır: Uzantı metodu yazma](./how-to-write-an-extension-method.md)
- [Genişletme Yöntemleri](./extension-methods.md)
- [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
