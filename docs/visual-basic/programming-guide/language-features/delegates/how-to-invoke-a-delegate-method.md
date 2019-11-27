---
title: 'Nasıl yapılır: Temsilci Yöntemi Çağırma'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: 520bacfbe6103490e0459cd5af149c1d55a8fce4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345261"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Nasıl yapılır: Temsilci Yöntemi Çağırma (Visual Basic)

Bu örnek, bir yöntemin bir temsilciyle nasıl ilişkilendirileceğini gösterir ve ardından bu yöntemi temsilci aracılığıyla çağırır.

### <a name="create-the-delegate-and-matching-procedures"></a>Temsilci ve eşleştirme yordamlarını oluşturma

1. `MySubDelegate`adlı bir temsilci oluşturun.

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

3. Temsilcinin bir örneğini oluşturan ve yerleşik `Invoke` yöntemini çağırarak temsilciyle ilişkili yöntemi çağıran bir yöntem tanımlayın.

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
