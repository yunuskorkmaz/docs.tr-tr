---
title: "Nasıl yapılır: Temsilci Yöntemi Çağırma (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ea94d4bb26e168667fd75c6928e52261f230c85e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Nasıl yapılır: Temsilci Yöntemi Çağırma (Visual Basic)
Bu örnek, bir yöntem bir temsilci ile ilişkilendirmek ve temsilci aracılığıyla bu yöntem çağırma gösterilmektedir.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Temsilci oluşturup eşleşen yordamları  
  
1.  Adlı bir temsilci oluşturma `MySubDelegate`.  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  Temsilci olarak aynı imzaya sahip bir yöntemi içeren bir sınıf bildirme.  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  Temsilci örneği oluşturur ve yerleşik çağırarak temsilci ile ilişkili yöntemi çağırır bir yöntemi tanımlamak `Invoke` yöntemi.  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Delegate deyimi](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Olayları](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Birden çok iş parçacıklı uygulamalar](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
