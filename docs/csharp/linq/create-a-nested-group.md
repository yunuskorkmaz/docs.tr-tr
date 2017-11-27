---
title: "İç içe geçmiş grup oluşturma"
description: "İç içe geçmiş grup oluşturma"
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
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
