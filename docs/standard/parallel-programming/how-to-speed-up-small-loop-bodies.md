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
ms.openlocfilehash: 29d7fa8200ddd972c1a5c98ea6f30a7c8ff732e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139755"
---
# <a name="how-to-speed-up-small-loop-bodies"></a>Nasıl yapılır: Küçük Döngü Gövdelerini Hızlandırma
Bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> döngü küçük bir gövdeye sahipse, C#'daki [for](../../csharp/language-reference/keywords/for.md) döngüsü ve Visual Basic'teki [For](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/44kykk21(v=vs.90)) döngüsü gibi eşdeğer sıralı döngüden daha yavaş çalışabilir. Daha yavaş performans, verilerin bölümlemesinde yer alan ek yükü ve her döngü yinelemesinde bir temsilci nin çağırılmasının maliyetinden kaynaklanır. Bu tür senaryoları <xref:System.Collections.Concurrent.Partitioner> gidermek için <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> sınıf, temsilci gövdesi için sıralı bir döngü sağlamanızı sağlayan yöntemi sağlar, böylece temsilci yineleme başına bir kez yerine bölüm başına yalnızca bir kez çağrılır. Daha fazla bilgi [için PLINQ ve TPL için Özel Bölümleyiciler'e](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)bakın.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Bu örnekte gösterilen yaklaşım, döngü en az miktarda çalışma gerçekleştirdiğinde yararlıdır. Çalışma daha hesaplamalı pahalı hale geldikçe, büyük olasılıkla varsayılan bölümleyici <xref:System.Threading.Tasks.Parallel.For%2A> <xref:System.Threading.Tasks.Parallel.ForEach%2A> ile bir veya döngü kullanarak aynı veya daha iyi performans alırsınız.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [PLINQ ve TPL için Özel Bölümleyiciler](../../../docs/standard/parallel-programming/custom-partitioners-for-plinq-and-tpl.md)
- [Yineleyiciler (C#)](../../csharp/programming-guide/concepts/iterators.md)
- [Yineleyiciler (Visual Basic)](../../visual-basic/programming-guide/concepts/iterators.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
