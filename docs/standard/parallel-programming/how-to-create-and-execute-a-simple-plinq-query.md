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
ms.openlocfilehash: a5f6a26ada321bd351249c5179d050ee571b550c
ms.sourcegitcommit: aa6d8a90a4f5d8fe0f6e967980b8c98433f05a44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2020
ms.locfileid: "90679350"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Nasıl yapılır: Basit bir PLINQ Sorgusu Oluşturma ve Yürütme

Bu makaledeki örnekte, kaynak dizideki genişletme yöntemi kullanılarak basit bir paralel dil tümleşik sorgu (LINQ) sorgusunun oluşturulması <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> ve yöntemi kullanılarak sorgu yürütülmesi gösterilmektedir <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithType> .  
  
> [!NOTE]
> Bu belgede, PLıNQ içinde temsilciler tanımlamak için lambda ifadeleri kullanılmaktadır. C# veya Visual Basic lambda ifadeleriyle ilgili bilgi sahibi değilseniz bkz. [PLıNQ ve TPL Içindeki lambda ifadeleri](lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Bu örnek, sonuç sırasının sıralaması önemli olmadığında herhangi bir paralel LINQ sorgusunun oluşturulması ve yürütülmesi için temel düzeni gösterir. Sıralanmamış sorgular genellikle sıralanmış sorgulardan daha hızlıdır. Sorgu, kaynağı birden çok iş parçacığında zaman uyumsuz olarak yürütülen görevlere bölümler. Her görevin tamamlandığı sıra, yalnızca bölümdeki öğeleri işlemek için gereken iş miktarına değil, aynı zamanda işletim sisteminin her bir iş parçacığını nasıl zamanlıyor gibi dış faktörlerden de farklı olur. Bu örnek, kullanımı göstermeye yöneliktir ve eşdeğer sıralı LINQ to Objects sorgusundan daha hızlı çalışmayabilir. Hızlı yedekleme hakkında daha fazla bilgi için bkz. [PLıNQ 'Te hızlı hızlandırı anlama](understanding-speedup-in-plinq.md). Bir sorgudaki öğelerin sıralamasını koruma hakkında daha fazla bilgi için bkz. [nasıl yapılır: PLıNQ sorgusunda sıralamayı denetleme](how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
