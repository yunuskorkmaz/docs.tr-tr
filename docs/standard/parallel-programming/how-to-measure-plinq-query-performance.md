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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd9e3a0ead62450e87225212f4fc6ecec6ec9489
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45618772"
---
# <a name="how-to-measure-plinq-query-performance"></a>Nasıl yapılır: PLINQ Sorgu Performansını Ölçme
Bu örnek nasıl kullanıldığını gösterir <xref:System.Diagnostics.Stopwatch> bir PLINQ sorgusu yürütmek gereken süreyi ölçmek için sınıf.  
  
## <a name="example"></a>Örnek  
 Bu örnekte boş `foreach` döngü (`For Each` Visual Basic'te) sorgu yürütmek gereken süreyi ölçmek için. Gerçek kod içinde döngü genellikle toplam sorgu yürütme süresini ekleme ek işleme adımları içerir. Kronometre değil dikkat edin, yalnızca kadar döngü önce olduğundan, ne zaman başladı sorgu yürütmeyi başlatır. Daha fazla hassas ölçüm gerektiriyorsa, kullanabileceğiniz `ElapsedTicks` özelliği yerine `ElapsedMilliseconds`.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Sorgu uygulamasıyla deneylerini ancak hikayenin tamamını her zaman söylemez yararlı bir ölçüm toplam yürütme süresi olur. Etkileşim sorgu iş parçacığı birbirleriyle ve diğer işlemleri çalıştırırken daha ayrıntılı ve daha zengin bir görünümünü elde etmek için Concurrency Visualizer'ı kullanın. Daha fazla bilgi için [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
