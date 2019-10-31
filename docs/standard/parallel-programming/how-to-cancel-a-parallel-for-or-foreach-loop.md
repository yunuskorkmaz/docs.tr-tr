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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134240"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemleri, iptal belirteçleri kullanılarak iptali destekler. Genel olarak iptal hakkında daha fazla bilgi için bkz. [iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md). Paralel bir döngüde, <xref:System.Threading.Tasks.ParallelOptions> parametresindeki yöntemine <xref:System.Threading.CancellationToken> sağlarsınız ve sonra bir try-catch bloğunda paralel çağrıyı içine almalısınız.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>çağrısının nasıl iptal edildiğini gösterir. <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> çağrısına aynı yaklaşımı uygulayabilirsiniz.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 İptali işaret eden belirteç <xref:System.Threading.Tasks.ParallelOptions> örneğinde belirtilen belirteçtir, paralel döngü iptal durumunda tek bir <xref:System.OperationCanceledException> oluşturur. Başka bir belirteç iptaline neden olursa, döngü bir InnerException olarak <xref:System.OperationCanceledException> bir <xref:System.AggregateException> oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
