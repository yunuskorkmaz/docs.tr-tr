---
title: Gruplandırma işleminde alt sorgu gerçekleştirme
description: Gruplandırma işleminde alt sorgu gerçekleştirme yapma.
ms.date: 12/1/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: 209d05c2fe8719fa9116061d199272366146f465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Gruplandırma işleminde alt sorgu gerçekleştirme

Bu konuda, gruplar halinde veri kaynağını sıralar ve ardından bir alt sorgu her grubu ayrı ayrı gerçekleştiren bir sorgu oluşturmak için iki farklı yolu gösterilmektedir. Temel her örnekte kullanarak kaynağı öğeleri gruplandırmak için tekniktir bir *devamlılık* adlı `newGroup`, yeni bir alt sorgu karşı oluşturmasını `newGroup`. Bu alt sorgu dış sorgu tarafından oluşturulan her yeni Grup karşı çalıştırılır. Bu örnekte son çıkışı değildir bir grup, ancak anonim türler düz bir dizi olduğuna dikkat edin.  
  
 Gruba hakkında daha fazla bilgi için bkz: [group yan tümcesi](../language-reference/keywords/group-clause.md).  
  
 Devamlılıklar hakkında daha fazla bilgi için bkz: [içine](../language-reference/keywords/into.md). Aşağıdaki örnek, veri kaynağı olarak bir bellek içi veri yapısı kullanır, ancak aynı ilkeler LINQ veri kaynağı herhangi bir tür için uygulanır.  
  
## <a name="example"></a>Örnek 

 > [!NOTE]
 > Bu örnek, örnek kodda tanımlanan nesnelere başvurular içerir [nesneler koleksiyonunu sorgulama](query-a-collection-of-objects.md).

 [!code-csharp[csProgGuideLINQ#23](../../../samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]  
   
## <a name="see-also"></a>Ayrıca bkz.  
 [LINQ Sorgu ifadeleri](index.md)
