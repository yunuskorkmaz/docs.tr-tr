---
title: 'Nasıl yapılır: PLINQ Sorgu Performansını Ölçme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to measure performance
ms.assetid: 491ba43b-2c10-473d-9aab-e2cb96446711
ms.openlocfilehash: 91b6165be2f4f464626fb25f7152de68de9d86e8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124990"
---
# <a name="how-to-measure-plinq-query-performance"></a>Nasıl yapılır: PLINQ Sorgu Performansını Ölçme
Bu örnek, bir PLıNQ sorgusunun yürütülmesi için geçen süreyi ölçmek için <xref:System.Diagnostics.Stopwatch> sınıfını nasıl kullanacağınızı gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, sorgunun yürütülmesi için geçen süreyi ölçmek üzere boş bir `foreach` döngüsünü (Visual Basic`For Each`) kullanır. Gerçek dünyada kodda, döngü genellikle toplam sorgu yürütme zamanına eklenen ek işleme adımları içerir. Sorgu yürütme başladığında, kronometre 'un döngüden önce başlamadığına dikkat edin. Daha ayrıntılı ölçüm gerekliyse, `ElapsedMilliseconds`yerine `ElapsedTicks` özelliğini kullanabilirsiniz.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Toplam yürütme süresi, sorgu uygulamalarıyla denemeler yaparken yararlı bir ölçümdür, ancak her zaman hikayenin tamamına söylemez. Sorgu iş parçacıklarının bir diğeri ve diğer çalışan işlemlerle etkileşimini daha ayrıntılı ve daha zengin bir şekilde görüntülemek için eşzamanlılık görselleştiricisi kullanın. Daha fazla bilgi için bkz. [Eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
