---
title: 'Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: 67f1f91f235cc88deaa97d412f368819ae0a8cda
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73134240"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme
Ve <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemler iptal belirteçleri kullanarak iptali destekler. Genel olarak iptal hakkında daha fazla bilgi için [İptal'e](../../../docs/standard/threading/cancellation-in-managed-threads.md)bakın. Paralel bir döngüde, <xref:System.Threading.CancellationToken> <xref:System.Threading.Tasks.ParallelOptions> yönteme parametreyi sağlarsınız ve paralel aramayı try-catch bloğuna içine alabilirsiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>'ye yapılan bir çağrının nasıl iptal edilebildiğini gösterir Aynı yaklaşımı bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> çağrıya da uygulayabilirsiniz.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 İptal sinyali veren <xref:System.Threading.Tasks.ParallelOptions> belirteç, örneğin belirtilen belirteçle aynıysa, paralel döngü <xref:System.OperationCanceledException> iptal de tek bir belirtme atar. Başka bir belirteç iptale neden <xref:System.AggregateException> olursa, <xref:System.OperationCanceledException> döngü bir InnerException olarak bir atacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
