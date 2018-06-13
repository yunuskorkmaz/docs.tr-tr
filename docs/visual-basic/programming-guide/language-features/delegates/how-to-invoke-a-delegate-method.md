---
title: 'Nasıl yapılır: Temsilci Yöntemi Çağırma (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: aca87dd9fa1990d44c99aab7753f2fd7d508adc1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646958"
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
 [Delegate Deyimi](../../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Temsilciler](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [Olaylar](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Çok İş Parçacıklı Uygulamalar](http://msdn.microsoft.com/library/a06a1a56-dd16-44e8-bc01-2c2255511bc6)
