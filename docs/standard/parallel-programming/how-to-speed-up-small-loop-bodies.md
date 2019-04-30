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
ms.openlocfilehash: fde68d0a938ed04380bf0e99cc0c544793571d77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61682982"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma
Olduğunda bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngüye sahip küçük bir gövde, eşdeğer sıralı döngü daha yavaş, gibi gerçekleştirebileceğiniz [için](../../csharp/language-reference/keywords/for.md) döngüde C# ve [için](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) Visual Basic'te döngü. Yavaş performans verileri ve her döngü yinelemesinin bir Temsilcide çağırma maliyeti Bölümlemede yükü nedeniyle oluşur. Bu tür senaryolara <xref:System.Collections.Concurrent.Partitioner> sağlar sınıfını <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> yöntemi temsilci gövdesi için sıralı döngü girmenize olanak tanır ve böylece temsilci yineleme başına bir kez yerine bir bölüm başına yalnızca bir kez çağrılır. Daha fazla bilgi için [PLINQ ve TPL için özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Bu örnekte gösterilen yaklaşım, döngünün en az miktarda iş gerçekleştirdiğinde kullanışlıdır. İş daha hesaplama açısından pahalı hale geldiğinde, büyük olasılıkla aynı veya daha iyi performans kullanarak erişmenizi sağlayacak bir <xref:System.Threading.Tasks.Parallel.For%2A> veya <xref:System.Threading.Tasks.Parallel.ForEach%2A> varsayılan bölümleyici ile döngüsü.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [Yineleyiciler (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Yineleyiciler (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
