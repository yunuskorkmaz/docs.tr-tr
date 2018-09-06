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
ms.openlocfilehash: 184b8408de45d0011a662b91905dade4c8826ec0
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723655"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma
Olduğunda bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngüye sahip küçük bir gövde, eşdeğer sıralı döngü daha yavaş, gibi gerçekleştirebileceğiniz [için](~/docs/csharp/language-reference/keywords/for.md) döngüde C# ve [için](https://msdn.microsoft.com/library/c470a263-9b49-4308-8fd6-8592b84a7980) Visual Basic'te döngü. Yavaş performans verileri ve her döngü yinelemesinin bir Temsilcide çağırma maliyeti Bölümlemede yükü nedeniyle oluşur. Bu tür senaryolara <xref:System.Collections.Concurrent.Partitioner> sağlar sınıfını <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> yöntemi temsilci gövdesi için sıralı döngü girmenize olanak tanır ve böylece temsilci yineleme başına bir kez yerine bir bölüm başına yalnızca bir kez çağrılır. Daha fazla bilgi için [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Bu örnekte gösterilen yaklaşım, döngünün en az miktarda iş gerçekleştirdiğinde kullanışlıdır. İş daha hesaplama açısından pahalı hale geldiğinde, büyük olasılıkla aynı veya daha iyi performans kullanarak erişmenizi sağlayacak bir <xref:System.Threading.Tasks.Parallel.For%2A> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A> varsayılan bölümleyici ile döngüsü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)  
 [Yineleyiciler](https://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
