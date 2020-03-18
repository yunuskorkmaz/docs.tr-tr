---
title: Gruplandırma işleminde bir alt sorgu gerçekleştirin (C#'da LINQ)
description: C#'da LINQ kullanarak gruplandırma işleminde bir alt sorgu nasıl gerçekleştirililir?
ms.date: 12/01/2016
ms.assetid: d75a588e-9b6f-4f37-b195-f99ec8503855
ms.openlocfilehash: fd26f87ad7d5b4892f086bf8c7a34cf19a7f9e02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173373"
---
# <a name="perform-a-subquery-on-a-grouping-operation"></a>Gruplandırma işleminde alt sorgu gerçekleştirme

Bu makalede, kaynak verileri gruplara ayıran bir sorgu oluşturmanın iki farklı yolu gösterilmektedir ve sonra her grup üzerinde ayrı ayrı bir alt sorgu gerçekleştirir. Her örnekte temel teknik, kaynak öğeleri adlı *continuation* `newGroup`bir devamı kullanarak gruplandırmak ve `newGroup`daha sonra karşı yeni bir alt sorgu oluşturmaktır. Bu alt sorgu, dış sorgu tarafından oluşturulan her yeni gruba karşı çalıştırılır. Bu özel örnekte son çıktının bir grup değil, anonim türlerin düz bir sırası olduğunu unutmayın.  
  
Gruplandırma hakkında daha fazla bilgi için [grup yan tümcesine](../language-reference/keywords/group-clause.md)bakın.  
  
Devamı hakkında daha fazla bilgi için [bkz.](../language-reference/keywords/into.md) Aşağıdaki örnek, veri kaynağı olarak bellek içi bir veri yapısı kullanır, ancak her tür LINQ veri kaynağı için aynı ilkeler geçerlidir.  
  
## <a name="example"></a>Örnek

> [!NOTE]
> Bu örnek, sorgulayan [nesneler koleksiyonunda](query-a-collection-of-objects.md)örnek kodda tanımlanan nesnelere başvurular içerir.

[!code-csharp[csProgGuideLINQ#23](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_1.cs)]

Yukarıdaki parçacıktaki sorgu yöntem sözdizimi kullanılarak da yazılabilir. Aşağıdaki kod snippet yöntem sözdizimi kullanılarak yazılmış bir semantically eşdeğer sorgu vardır.

[!code-csharp[csProgGuideLINQ#86](~/samples/snippets/csharp/concepts/linq/how-to-perform-a-subquery-on-a-grouping-operation_2.cs)]

## <a name="see-also"></a>Ayrıca bkz.

- [Dil ile Tümleşik Sorgu (LINQ)](index.md)
