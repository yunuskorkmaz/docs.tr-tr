---
title: Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 85798e6453bc6cea6174ecc536b35835865e0459
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163460"
---
# <a name="bc36647-and-bc36644-data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>BC36647 ve BC36644: tür parametrelerinin veri türleri bu bağımsız değişkenlerden çıkarılamıyor

Tür parametrelerinin veri türleri bu bağımsız değişkenlerden çıkarılamıyor. Veri türlerinin açıkça belirtilmesi bu hatayı düzeltebilir.

Aşırı yükleme çözümlemesi başarısız olduğunda bu hata oluşur. Belirli bir aşırı yükleme adayını neden ortadan kaldırmadığını belirten bir alt ileti olarak gerçekleşir. Hata mesajı, derleyicinin tür çıkarımı için veri türlerini bulmak için tür çıkarımı kullanamadığını açıklar.

> [!NOTE]
> Bağımsız değişkenlerin belirtilmesi bir seçenek değil (örneğin, sorgu ifadelerinde sorgu işleçleri için), ikinci tümce olmadan hata iletisi görüntülenir.

Aşağıdaki kod hatayı gösterir.

```vb
Module Module1

    Sub Main()

        '' Not Valid.
        'OverloadedGenericMethod("Hello", "World")

    End Sub

    Sub OverloadedGenericMethod(Of T)(ByVal x As String,
                                      ByVal y As InterfaceExample(Of T))
    End Sub

    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,
                                         ByVal y As InterfaceExample(Of R))
    End Sub

End Module

Interface InterfaceExample(Of T)
End Interface
```

**Hata kimliği:** BC36647 ve BC36644

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Tür çıkarımı güvenmek yerine tür parametresi veya parametreleri için bir veri türü belirtebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Gevşek Temsilci Dönüştürme](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Visual Basic'de Genel Yordamlar](../../programming-guide/language-features/data-types/generic-procedures.md)
- [Visual Basic'de Tür Dönüştürmeleri](../../programming-guide/language-features/data-types/type-conversions.md)
