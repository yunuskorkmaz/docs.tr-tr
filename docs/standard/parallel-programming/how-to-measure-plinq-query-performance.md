---
description: 'Şu konuda daha fazla bilgi edinin: nasıl yapılır: PLıNQ sorgu performansını ölçme'
title: 'Nasıl yapılır: PLINQ Sorgu Performansını Ölçme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: b8b447e49c725155559d910708a0b09c104a663f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99701813"
---
# <a name="how-to-measure-plinq-query-performance"></a>Nasıl yapılır: PLINQ Sorgu Performansını Ölçme

Bu örnek, <xref:System.Diagnostics.Stopwatch> BIR PLıNQ sorgusunun yürütülmesi için geçen süreyi ölçmek için sınıfını nasıl kullanacağınızı gösterir.  
  
## <a name="example"></a>Örnek  

 Bu örnek `foreach` `For Each` , sorgunun yürütülmesi için gereken süreyi ölçmek üzere boş bir döngü (Visual Basic olarak) kullanır. Gerçek dünyada kodda, döngü genellikle toplam sorgu yürütme zamanına eklenen ek işleme adımları içerir. Sorgu yürütme başladığında, kronometre 'un döngüden önce başlatıldığına dikkat edin. Daha ayrıntılı ölçüm gerekiyorsa, `ElapsedTicks` bunun yerine özelliğini kullanabilirsiniz `ElapsedMilliseconds` .  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Toplam yürütme süresi, sorgu uygulamalarıyla denemeler yaparken yararlı bir ölçümdür, ancak her zaman hikayenin tamamına söylemez. Sorgu iş parçacıklarının bir diğeri ve diğer çalışan işlemlerle etkileşimini daha ayrıntılı ve daha zengin bir şekilde görüntülemek için [Eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer)kullanın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](introduction-to-plinq.md)
