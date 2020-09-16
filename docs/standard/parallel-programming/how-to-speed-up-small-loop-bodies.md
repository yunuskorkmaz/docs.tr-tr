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
ms.openlocfilehash: c91aecee226b52d9045f3bd95a05c234abac8c96
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548318"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma
Bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngünün küçük bir gövdesi olduğunda, C# ' deki [for](../../csharp/language-reference/keywords/for.md) döngüsü ve Visual Basic [for](/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) döngüsü gibi eşdeğer sıralı döngüden daha yavaş çalışabilir. Verilerin bölümlenmesi ve her döngü yinelemesinde bir temsilciyi çağırma maliyeti nedeniyle daha yavaş performans oluşur. Bu tür senaryolara yönelik olarak, <xref:System.Collections.Concurrent.Partitioner> sınıfı, temsilci <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> gövdesi için sıralı bir döngü sağlamanıza olanak tanıyan yöntemini sağlar. böylece, temsilci her yineleme için bir kez değil, her bölüm için yalnızca bir kez çağırılır. Daha fazla bilgi için bkz. [PLıNQ ve TPL Için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Bu örnekte gösterilen yaklaşım, döngü en az miktarda iş gerçekleştirdiğinde kullanışlıdır. Çalışma daha pahalı hale geldiği için, <xref:System.Threading.Tasks.Parallel.For%2A> varsayılan bölümleyici ile veya döngüsünü kullanarak büyük olasılıkla aynı veya daha iyi bir performans alacaksınız <xref:System.Threading.Tasks.Parallel.ForEach%2A> .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri paralelliği](data-parallelism-task-parallel-library.md)
- [PLıNQ ve TPL için Özel Bölümleyiciler](custom-partitioners-for-plinq-and-tpl.md)
- [Yineleyiciler (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Yineleyiciler (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [PLıNQ ve TPL 'deki lambda Ifadeleri](lambda-expressions-in-plinq-and-tpl.md)
