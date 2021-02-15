---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: temsilci yöntemi çağırma (Visual Basic)'
title: 'Nasıl yapılır: Temsilci Yöntemi Çağırma'
ms.date: 07/20/2015
ms.assetid: b56866ae-abf9-4a5a-a855-486359455e9c
ms.openlocfilehash: c5c20048969f2fef16b8b7f65e84a094a3f1cf9f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434478"
---
# <a name="how-to-invoke-a-delegate-method-visual-basic"></a>Nasıl yapılır: Temsilci Yöntemi Çağırma (Visual Basic)

Bu örnek, bir yöntemin bir temsilciyle nasıl ilişkilendirileceğini gösterir ve ardından bu yöntemi temsilci aracılığıyla çağırır.

### <a name="create-the-delegate-and-matching-procedures"></a>Temsilci ve eşleştirme yordamlarını oluşturma

1. Adlı bir temsilci oluşturun `MySubDelegate` .

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

3. Temsilcinin bir örneğini oluşturan ve yerleşik metodu çağırarak temsilciyle ilişkili yöntemi çağıran bir yöntem tanımlayın `Invoke` .

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

- [Delegate Deyimi](../../../language-reference/statements/delegate-statement.md)
- [Temsilciler](index.md)
- [Ekinlikler](../events/index.md)
- [Çok İş Parçacıklı Uygulamalar](../../../../standard/threading/using-threads-and-threading.md)
