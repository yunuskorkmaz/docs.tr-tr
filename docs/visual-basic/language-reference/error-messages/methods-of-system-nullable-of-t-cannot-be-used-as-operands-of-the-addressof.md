---
title: "'System.Nullable(Of T)' yöntemleri 'AddressOf' işlecinin işlenenleri olarak kullanılamaz"
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: e55e561fa20a3740d352537958681b0a66fc381e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592038"
---
# <a name="methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a>'System.Nullable(Of T)' yöntemleri 'AddressOf' işlecinin işlenenleri olarak kullanılamaz
Bir ifade kullanıyor `AddressOf` işleci, bir yordamı temsil eden bir işlenen <xref:System.Nullable%601> yapısı.  
  
 **Hata Kimliği:** BC32126  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Yordam adı yerine `AddressOf` yan tümcesi bir üyesi değil bir işlenen <xref:System.Nullable%601>.  
  
- Yazma yöntemi saran bir sınıf <xref:System.Nullable%601> kullanmak istediğiniz. Aşağıdaki örnekte, `NullableWrapper` sınıf adlı yeni bir yöntem tanımlar `GetValueOrDefault`. Bu yeni yöntemi üyesi olmadığından <xref:System.Nullable%601>, için uygulanabilir `nullInstance`, bir bağımsız değişken oluşturmak için boş değer atanabilir bir tür örneği `AddressOf`.  
  
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
