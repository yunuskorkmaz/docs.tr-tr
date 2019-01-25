---
title: 'Nasıl yapılır: (Visual Basic) temsilci yöntemi çağırma'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: 42d56fca7e1d33c071db2e7e38935aa00caa5b7d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676217"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Nasıl yapılır: (Visual Basic) temsilci yöntemi çağırma
Bu örnek, bir yöntem bir temsilci ile ilişkilendirin ve ardından o yöntemi temsilci aracılığıyla çağırmak nasıl gösterir.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Temsilci ve eşleşen yordamlar oluşturma  
  
1.  Adlı bir temsilci oluşturmak `MySubDelegate`.  
  
    ```  
    Delegate Sub MySubDelegate(ByVal x As Integer)  
    ```  
  
2.  Temsilci olarak aynı imzaya sahip bir yöntemi içeren bir sınıfı bildirir.  
  
    ```  
    Class class1  
        Sub Sub1(ByVal x As Integer)  
            MsgBox("The value of x is: " & CStr(x))  
        End Sub  
    End Class  
    ```  
  
3.  Temsilci örneği oluşturur ve temsilci ile yerleşik çağırarak ilişkili yöntemi çağırır bir yöntemi tanımlamak `Invoke` yöntemi.  
  
    ```  
    Protected Sub DelegateTest()  
        Dim c1 As New class1  
        ' Create an instance of the delegate.  
        Dim msd As MySubDelegate = AddressOf c1.Sub1  
        ' Call the method.  
        msd.Invoke(10)  
    End Sub  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Delegate Deyimi](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [Çok İş Parçacıklı Uygulamalar](../../../../standard/threading/using-threads-and-threading.md)
