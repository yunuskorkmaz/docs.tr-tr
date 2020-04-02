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
ms.openlocfilehash: 4cb0d408798d66c8491654c90f33255c700690a3
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80587789"
---
# <a name="how-to-measure-plinq-query-performance"></a>Nasıl yapılır: PLINQ Sorgu Performansını Ölçme
Bu örnek, bir <xref:System.Diagnostics.Stopwatch> PLINQ sorgusunun yürütülmesi için gereken süreyi ölçmek için sınıfın nasıl kullanıldığını gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, `foreach` sorgunun`For Each` yürütülmesi için gereken süreyi ölçmek için boş bir döngü (Visual Basic'te) kullanır. Gerçek dünya kodunda, döngü genellikle toplam sorgu yürütme süresine ekleyen ek işleme adımları içerir. Kronometrenin döngüden hemen öncesine kadar başlatılmadığını, çünkü sorgu yürütmesinin başladığı zaman olduğuna dikkat edin. Daha ince taneli ölçüm eihtiyacınız varsa, `ElapsedTicks` özelliği `ElapsedMilliseconds`' nin yerine kullanabilirsiniz.  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 Sorgu uygulamalarıyla deneme yaparken toplam yürütme süresi yararlı bir ölçüdür, ancak her zaman tüm hikayeyi anlatmaz. Sorgu iş parçacıklarının birbirleriyle ve diğer çalışan işlemlerle etkileşimini daha derin ve daha zengin bir görünüme sahip etmek için Eşzamanlılık Görselleştiricisini kullanın. Daha fazla bilgi için [Concurrency Visualizer'a](/visualstudio/profiling/concurrency-visualizer)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Paralel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
