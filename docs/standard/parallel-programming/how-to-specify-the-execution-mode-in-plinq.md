---
title: "Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c1c815131a1553001cdcf20e3c7408e472299677
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Nasıl yapılır: PLINQ'te Yürütme Modunu Belirtme
Bu örnek varsayılan buluşsal atlamak için bir sorgu sorgu şekli bağımsız olarak paralel hale PLINQ zorlamak nasıl gösterir.  
  
> [!WARNING]
>  Bu örnek kullanım göstermeye yöneliktir ve eşdeğer sıralı LINQ daha hızlı nesneleri sorguya çalışmayabilir. Speedup hakkında daha fazla bilgi için bkz: [Plınq'te hızlandırmayı anlama](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ paralelleştirme olanaklarını yararlanmak için tasarlanmıştır. Ancak, tüm sorguları paralel yürütülmesini yararlanır. Sorguda çok az şey yapan bir tek kullanıcı temsilci içeriyorsa, örneğin, sorgu genellikle daha hızlı sırayla çalışır. Parallelizing yürütme etkinleştirme söz konusu yükünü alınır speedup daha pahalı olmasıdır. Bu nedenle, PLINQ otomatik olarak her sorguyu paralel hale değil. Önce sorgu ve onu oluşturan çeşitli işleçler şeklini inceler. Bu analize dayalı olarak, varsayılan yürütme modu PLINQ'te bazılarını veya tümünü sorgu sırayla yürütmek karar verebilirsiniz. PLINQ kendi çözümlemesinden belirlemek mümkün olandan ancak, bazı durumlarda, daha sorgunuzu hakkında bilmeniz. Örneğin, bir temsilci çok pahalı olduğunu ve sorgu paralelleştirme kesinlikle faydalanırsınız biliyorsunuz. Böyle durumlarda, kullandığınız <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> yöntemi ve belirtin <xref:System.Linq.ParallelExecutionMode.ForceParallelism> değer her zaman sorguyu paralel çalıştırmak için PLINQ isteyin.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu kodu kesip [PLINQ veri örneği](../../../docs/standard/parallel-programming/plinq-data-sample.md) ve yöntemi çağırın `Main`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
