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
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43867235"
---
# <a name="how-to-measure-plinq-query-performance"></a><span data-ttu-id="1d785-102">Nasıl yapılır: PLINQ Sorgu Performansını Ölçme</span><span class="sxs-lookup"><span data-stu-id="1d785-102">How to: Measure PLINQ Query Performance</span></span>
<span data-ttu-id="1d785-103">Bu örnek nasıl kullanıldığını gösterir <xref:System.Diagnostics.Stopwatch> bir PLINQ sorgusu yürütmek gereken süreyi ölçmek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="1d785-103">This example shows how use the <xref:System.Diagnostics.Stopwatch> class to measure the time it takes for a PLINQ query to execute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d785-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1d785-104">Example</span></span>  
 <span data-ttu-id="1d785-105">Bu örnekte boş `foreach` döngü (`For Each` Visual Basic'te) sorgu yürütmek gereken süreyi ölçmek için.</span><span class="sxs-lookup"><span data-stu-id="1d785-105">This example uses an empty `foreach` loop (`For Each` in Visual Basic) to measure the time it takes for the query to execute.</span></span> <span data-ttu-id="1d785-106">Gerçek kod içinde döngü genellikle toplam sorgu yürütme süresini ekleme ek işleme adımları içerir.</span><span class="sxs-lookup"><span data-stu-id="1d785-106">In real-world code, the loop typically contains additional processing steps that add to the total query execution time.</span></span> <span data-ttu-id="1d785-107">Kronometre değil dikkat edin, yalnızca kadar döngü önce olduğundan, ne zaman başladı sorgu yürütmeyi başlatır.</span><span class="sxs-lookup"><span data-stu-id="1d785-107">Notice that the stopwatch is not started until just before the loop, because that is when the query execution begins.</span></span> <span data-ttu-id="1d785-108">Daha fazla hassas ölçüm gerektiriyorsa, kullanabileceğiniz `ElapsedTicks` özelliği yerine `ElapsedMilliseconds`.</span><span class="sxs-lookup"><span data-stu-id="1d785-108">If you require more fine-grained measurement, you can use the `ElapsedTicks` property instead of `ElapsedMilliseconds`.</span></span>  
  
 [!code-csharp[PLINQ#19](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/measure2.cs#19)]
 [!code-vb[PLINQ#19](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/measure2.vb#19)]  
  
 <span data-ttu-id="1d785-109">Sorgu uygulamasıyla deneylerini ancak hikayenin tamamını her zaman söylemez yararlı bir ölçüm toplam yürütme süresi olur.</span><span class="sxs-lookup"><span data-stu-id="1d785-109">The total execution time is a useful metric when you are experimenting with query implementations, but it does not always tell the whole story.</span></span> <span data-ttu-id="1d785-110">Etkileşim sorgu iş parçacığı birbirleriyle ve diğer işlemleri çalıştırırken daha ayrıntılı ve daha zengin bir görünümünü elde etmek için Concurrency Visualizer'ı kullanın.</span><span class="sxs-lookup"><span data-stu-id="1d785-110">To get a deeper and richer view of the interaction of the query threads with one another and with other running processes, use the Concurrency Visualizer.</span></span> <span data-ttu-id="1d785-111">Daha fazla bilgi için [eşzamanlılık görselleştiricisi](/visualstudio/profiling/concurrency-visualizer).</span><span class="sxs-lookup"><span data-stu-id="1d785-111">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d785-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d785-112">See also</span></span>

- [<span data-ttu-id="1d785-113">Paralel LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="1d785-113">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
