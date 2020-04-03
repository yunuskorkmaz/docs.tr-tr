---
title: 'Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: c4cd75e55aabb551e5951a902ea6394a5659c9ee
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635849"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme

Bu makaledeki örnek, kaynak dizideki uzantı yöntemini <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> kullanarak ve <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> yöntemi kullanarak sorguyu yürüterek basit bir Paralel Dil Tümleşik Sorgusu (LINQ) sorgusunun nasıl oluşturuluğun gösteriş olduğunu göstermektedir.  
  
> [!NOTE]
> Bu dokümantasyon PLINQ'daki delegeleri tanımlamak için lambda ifadelerini kullanır. C# veya Visual Basic'teki lambda ifadelerine aşina değilseniz, [PLINQ ve TPL'deki Lambda İfadeleri'ne](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)bakın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Bu örnek, sonuç sırasının sıralanması önemli olmadığında, herhangi bir Paralel LINQ sorgusu oluşturmak ve yürütmek için temel deseni gösterir. Sıralanmamış sorgular genellikle sıralanan sorgulardan daha hızlıdır. Sorgu, kaynağı birden çok iş parçacığı üzerinde eşit olarak yürütülen görevlere bölümlere ayırır. Her görevin tamamlanma sırası yalnızca bölümdeki öğeleri işlemek için ilgili çalışma miktarına değil, aynı zamanda işletim sisteminin her iş parçacığının nasıl zamanladığı gibi dış etkenlere de bağlıdır. Bu örnek, kullanımı göstermek için tasarlanmıştır ve Nesneler sorgusuna eşdeğer ardışık LINQ'dan daha hızlı çalışmayabilir. Hız hakkında daha fazla bilgi için [PLINQ'da Hızları Anlama'ya](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md)bakın. Bir sorgudaki öğelerin sıralanması nın nasıl korunduğu hakkında daha fazla bilgi için [bkz.](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
