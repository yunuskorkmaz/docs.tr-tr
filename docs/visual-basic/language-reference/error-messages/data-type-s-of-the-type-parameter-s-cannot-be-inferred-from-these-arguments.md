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
ms.openlocfilehash: 4167905ca6ddab66b2cbc6c8c40dc7c984e94b8b
ms.sourcegitcommit: e08b319358a8025cc6aa38737854f7bdb87183d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/29/2019
ms.locfileid: "64913188"
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor
Yöntemindeki tür parametrelerinin veri türleri bu bağımsız değişkenlerden çıkarsanamıyor. Verileri belirleyerek türleri açıkça bu hatayı düzeltebilir.  
  
 Aşırı yükleme çözümlemesi başarısız olduğunda bu hata oluşur. Belirli bir aşırı yükleme aday neden ortadan kaldırılmıştır bildiren bir alt ileti gerçekleşir. Hata iletisi, tür parametreleri için veri türlerini bulmak için derleyicinin tür çıkarımı kullanamazsınız açıklar.  
  
> [!NOTE]
>  Bağımsız değişkenleri belirtme (örneğin, sorgu işleçleri için sorgu ifadelerinde) bir seçenek olmadığı durumlarda, ikinci cümlesi hata iletisi görüntülenir.  
  
 Aşağıdaki kod, hatayı gösterir.  
  
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
  
 **Hata Kimliği:** BC36647 ve BC36644  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Tür parametresi veya tür çıkarımı üzerinde kalmak yerine parametreleri için bir veri türü belirtmek mümkün olabilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Gevşek Temsilci Dönüştürme](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Visual Basic'de genel yordamlar](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)
- [Visual Basic'de tür dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
