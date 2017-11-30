---
title: "Nasıl yapılır: Uzantı Metodu Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- calling extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: df07750f-40f4-4c07-a79e-1113a27cfbea
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 25b5a86af15694e6f64f96a5d5d645a01f8f1f12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Nasıl yapılır: uzantı yöntemi yazma](./how-to-write-an-extension-method.md)  
 [Genişletme yöntemleri](./extension-methods.md)  
 [Visual Basic'de kapsam](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
