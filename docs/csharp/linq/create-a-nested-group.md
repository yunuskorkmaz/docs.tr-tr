---
title: İç içe geçmiş grup oluşturma
description: İç içe geçmiş grup oluşturma
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: dd1158bfa1456342fe8967aed5e02ecebae591c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273149"
---
# <a name="create-a-nested-group"></a>İç içe geçmiş grup oluşturma

Aşağıdaki örnekte bir LINQ sorgu ifadesinde iç içe grupları oluşturmayı gösterir. Öğrenci yıl veya notu düzeyine göre oluşturulan her bir grup sonra başka kişiler adlarına göre gruplara bölünmüştür.  
  
## <a name="example"></a>Örnek

 > [!NOTE]
 > Bu örnek, örnek kodda tanımlanan nesnelere başvurular içerir [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md). 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 Üç iç içe geçmiş Not `foreach` döngüler, iç içe geçmiş Grup iç öğeleri yineleme için gereklidir.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [LINQ Sorgu ifadeleri](index.md)
