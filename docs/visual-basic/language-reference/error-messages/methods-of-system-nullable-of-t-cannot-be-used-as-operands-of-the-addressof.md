---
title: "'System.Nullable(Of T)' yöntemleri 'AddressOf' işlecinin işlenenleri olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 54d66a60d20a6add4c2b4a160f87b58b5a1d00e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817272"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>'System.Nullable(Of T)' yöntemleri 'AddressOf' işlecinin işlenenleri olarak kullanılamaz
Bir ifade kullanıyor `AddressOf` işleci, bir yordamı temsil eden bir işlenen <xref:System.Nullable%601> yapısı.  
  
 **Hata Kimliği:** BC32126  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Yordam adı yerine `AddressOf` yan tümcesi bir üyesi değil bir işlenen <xref:System.Nullable%601>.  
  
-   Yazma yöntemi saran bir sınıf <xref:System.Nullable%601> kullanmak istediğiniz. Aşağıdaki örnekte, `NullableWrapper` sınıf adlı yeni bir yöntem tanımlar `GetValueOrDefault`. Bu yeni yöntemi üyesi olmadığından <xref:System.Nullable%601>, için uygulanabilir `nullInstance`, bir bağımsız değişken oluşturmak için boş değer atanabilir bir tür örneği `AddressOf`.  
  
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
- [AddressOf İşleci](../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Boş Değer Atanabilen Değer Türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Visual Basic'de genel türler](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
