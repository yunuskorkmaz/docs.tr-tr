---
title: "Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme"
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c67b23da6742af3cb65da6da49dbab982a0248bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683203"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme
Bu örnekte, varsayılan buluşsal atlamak ve sorgunun şekli bağımsız olarak bir sorgu paralel hale getirmek için PLINQ zorlamak gösterilmektedir.  
  
> [!WARNING]
>  Bu örnek, kullanımını göstermek için tasarlanmıştır ve nesneleri sorgu için eşdeğer sıralı LINQ daha hızlı çalışmayabilir. Hızlandırmayı hakkında daha fazla bilgi için bkz: [plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ, paralelleştirme için fırsatlar yararlanmak için tasarlanmıştır. Ancak, tüm sorguları paralel yürütmeyi yararlanır. Çok az çalışır bir tek kullanıcı temsilcisi bir sorgu içeriyor, örneğin, sorgu genellikle daha hızlı bir şekilde sırayla çalışır. Paralel yürütme etkinleştirirken yükü elde edilen hızlandırmayı daha ucuz olmasıdır. Bu nedenle, PLINQ otomatik olarak her bir sorguyu paralelleştirmesi değil. Öncelikle, sorgu ve onu oluşturan çeşitli işleçler şeklini inceler. Bu analizi temel alarak, PLINQ varsayılan yürütme modunda bazılarını veya tümünü sorgu ardışık olarak yürütmek karar verebilirsiniz. PLINQ, analiz belirlemek mümkün olandan ancak bazı durumlarda daha sorgunuzu hakkında haberdar olabilirsiniz. Örneğin, bir temsilci çok pahalı olduğundan ve sorgunun paralelleştirme kesinlikle faydalanır haberdar olabilirsiniz. Bu gibi durumlarda, kullandığınız <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemi belirtin <xref:System.Linq.ParallelExecutionMode.ForceParallelism> değeri her zaman sorguyu paralel çalıştırmak için PLINQ bildirin.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu kesip [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) ve içinden yöntemi çağırın `Main`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
