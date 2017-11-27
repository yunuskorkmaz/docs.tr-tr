---
title: "Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma"
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
helpviewer_keywords: parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d38d8beedf342720d4dc68026297edb457f5ed35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma
Zaman bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngü sahip küçük bir gövde, eşdeğer sıralı döngü daha yavaş onu gibi gerçekleştirebileceğiniz [için](~/docs/csharp/language-reference/keywords/for.md) döngü C# ve [için](http://msdn.microsoft.com/en-us/c470a263-9b49-4308-8fd6-8592b84a7980) Visual Basic'te döngü. Performans verileri ve temsilci her döngü tekrarında üzerinde çağırma maliyet bölümlendirme söz konusu yükünü kaynaklanır. Bu tür senaryosu için <xref:System.Collections.Concurrent.Partitioner> sınıfı sağlar <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> temsilci gövdesi için sıralı döngü vermenizi sağlar ve böylece temsilci yineleme başına bir kez yerine bölüm başına yalnızca bir kez çağrılır yöntemi. Daha fazla bilgi için bkz: [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Bu örnekte gösterilen yaklaşım, döngü iş en az miktarda gerçekleştirdiğinde kullanışlıdır. İş pkı'ya daha pahalı hale geldiğinde, büyük olasılıkla aynı veya daha iyi performans kullanarak karşılaşırsınız bir <xref:System.Threading.Tasks.Parallel.For%2A> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü varsayılan bölümleyici ile.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Yineleyiciler](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [PLINQ ve TPL'deki lambda ifadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
