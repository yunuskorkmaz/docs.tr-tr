---
description: "Hakkında daha fazla bilgi edinin: BC32126: ' System. Nullable (Of T) ' metotları ' AddressOf ' işlecinin işlenenleri olarak kullanılamaz"
title: "'System.Nullable(Of T)' yöntemleri 'AddressOf' işlecinin işlenenleri olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 5ddf2f11bab3193423a3294a7f96afe68f0e5dce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795800"
---
# <a name="bc32126-methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>BC32126: ' System. Nullable (Of T) ' metotları ' AddressOf ' işlecinin işlenenleri olarak kullanılamaz

Bir ifade, `AddressOf` Yapı yordamını temsil eden bir işlenen ile işlecini kullanır <xref:System.Nullable%601> .

 **Hata kimliği:** BC32126

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Yan tümcesindeki yordam adını, `AddressOf` üyesi olmayan bir işlenen ile değiştirin <xref:System.Nullable%601> .

- Kullanmak istediğiniz yöntemini sarmalayan bir sınıf yazın <xref:System.Nullable%601> . Aşağıdaki örnekte, `NullableWrapper` sınıfı adlı yeni bir yöntemi tanımlar `GetValueOrDefault` . Bu yeni yöntem bir üyesi olmadığından, <xref:System.Nullable%601> `nullInstance` için bir bağımsız değişken oluşturmak üzere null yapılabilir bir türün örneği olan öğesine uygulanabilir `AddressOf` .

```vb
Module Module1

    Delegate Function Deleg() As Integer

    Sub Main()
        Dim nullInstance As New Nullable(Of Integer)(1)

        Dim del As Deleg

        ' GetValueOrDefault is a method of the Nullable generic
        ' type. It cannot be used as an operand of AddressOf.
        ' del = AddressOf nullInstance.GetValueOrDefault

        ' The following line uses the GetValueOrDefault method
        ' defined in the NullableWrapper class.
        del = AddressOf (New NullableWrapper(
            Of Integer)(nullInstance)).GetValueOrDefault

        Console.WriteLine(del.Invoke())
    End Sub

    Class NullableWrapper(Of T As Structure)
        Private m_Value As Nullable(Of T)

        Sub New(ByVal Value As Nullable(Of T))
            m_Value = Value
        End Sub

        Public Function GetValueOrDefault() As T
            Return m_Value.Value
        End Function
    End Class
End Module
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Nullable%601>
- [AddressOf İşleci](../operators/addressof-operator.md)
- [Null yapılabilir değer türleri](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Visual Basic genel türler](../../programming-guide/language-features/data-types/generic-types.md)
