---
title: 'Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to speed up
ms.assetid: c7a66677-cb59-4cbf-969a-d2e8fc61a6ce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bff41416dd2263c185cc94de045b2c8a26ea194d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581157"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma
Zaman bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngü sahip küçük bir gövde, eşdeğer sıralı döngü daha yavaş onu gibi gerçekleştirebileceğiniz [için](~/docs/csharp/language-reference/keywords/for.md) döngü C# ve [için](http://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) Visual Basic'te döngü. Performans verileri ve temsilci her döngü tekrarında üzerinde çağırma maliyet bölümlendirme söz konusu yükünü kaynaklanır. Bu tür senaryosu için <xref:System.Collections.Concurrent.Partitioner> sınıfı sağlar <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> temsilci gövdesi için sıralı döngü vermenizi sağlar ve böylece temsilci yineleme başına bir kez yerine bölüm başına yalnızca bir kez çağrılır yöntemi. Daha fazla bilgi için bkz: [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Bu örnekte gösterilen yaklaşım, döngü iş en az miktarda gerçekleştirdiğinde kullanışlıdır. İş pkı'ya daha pahalı hale geldiğinde, büyük olasılıkla aynı veya daha iyi performans kullanarak karşılaşırsınız bir <xref:System.Threading.Tasks.Parallel.For%2A> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A> döngü varsayılan bölümleyici ile.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Yineleyiciler](https://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
