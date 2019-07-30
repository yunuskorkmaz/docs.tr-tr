---
title: 'Nasıl yapılır: Temsilci yöntemini çağır (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c2bdb65c9d060e854db3319e4aa5b2e93b9681af
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629583"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Nasıl yapılır: Temsilci yöntemini çağır (Visual Basic)

Bu örnek, bir yöntemin bir temsilciyle nasıl ilişkilendirileceğini gösterir ve ardından bu yöntemi temsilci aracılığıyla çağırır.

### <a name="create-the-delegate-and-matching-procedures"></a>Temsilci ve eşleştirme yordamlarını oluşturma

1. Adlı `MySubDelegate`bir temsilci oluşturun.

    ```vb
    Delegate Sub MySubDelegate(ByVal x As Integer)
    ```

2. Temsilciyle aynı imzaya sahip bir yöntem içeren bir sınıf bildirin.

    ```vb
    Class class1
        Sub Sub1(ByVal x As Integer)
            MsgBox("The value of x is: " & CStr(x))
        End Sub
    End Class
    ```

3. Temsilcinin bir örneğini oluşturan ve yerleşik `Invoke` metodu çağırarak temsilciyle ilişkili yöntemi çağıran bir yöntem tanımlayın.

    ```vb
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
