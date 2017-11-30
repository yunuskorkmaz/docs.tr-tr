---
title: "Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b290c25286dce2236823919e8287db9abefc0dd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor
Bu bağımsız değişkenlerden tür parametrelerinin veri türleri çıkarılamıyor. Verileri belirten türlerini açıkça bu hatayı düzeltmek.  
  
 Aşırı yükleme çözünürlüğü başarısız olduğunda bu hata oluşur. Neden belirli aşırı aday ortadan kaldırılmıştır bildiren bir alt ileti gerçekleşir. Hata iletisi, veri türleri için tür parametreleri bulmak için derleyici tür çıkarımı kullanamazsınız açıklanmaktadır.  
  
> [!NOTE]
>  Bağımsız değişkenleri (örneğin, sorgu işleçleri için sorgu ifadelerinde) bir seçenek olmadığı durumlarda, ikinci cümlesi hata iletisi görüntülenir.  
  
 Aşağıdaki kod hata gösterir.  
  
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
  
-   Tür parametresi veya tür çıkarımı kalmak yerine parametreleri için bir veri türü belirtmek mümkün olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Gevşek temsilci dönüşümü](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Visual Basic'de genel yordamlar](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
