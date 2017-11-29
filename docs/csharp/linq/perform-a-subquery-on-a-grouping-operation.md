---
title: "Gruplandırma işleminde alt sorgu gerçekleştirme"
description: "Gruplandırma işleminde alt sorgu gerçekleştirme yapma."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: f638b8a679a15891d04e02f1597d6bf7934a9e74
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2017
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
