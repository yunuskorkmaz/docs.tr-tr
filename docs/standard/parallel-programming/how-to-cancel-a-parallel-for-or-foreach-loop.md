---
title: 'Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme'
description: ParallelOptions parametresindeki yöntemine bir iptal belirteci nesnesi sağlayarak .NET 'teki bir Parallel. for veya Parallel. ForEach döngüsünü iptal edin.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
ms.openlocfilehash: 0a22794f3c45e685a80d36a42ecd849461936c7b
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769008"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>Ve yöntemleri, iptal <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> belirteçlerini kullanarak iptali destekler. Genel olarak iptal hakkında daha fazla bilgi için bkz. [iptal](../threading/cancellation-in-managed-threads.md). Paralel bir döngüde, <xref:System.Threading.CancellationToken> <xref:System.Threading.Tasks.ParallelOptions> parametresini parametresindeki yöntemine sağlarsınız ve sonra paralel çağrıyı bir try-catch bloğuna çevrelemelisiniz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir çağrısının nasıl iptal edildiğini gösterir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> . Bir çağrıya aynı yaklaşımı uygulayabilirsiniz <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> .  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 İptaline işaret eden belirteç örnekte belirtilen belirteçtir <xref:System.Threading.Tasks.ParallelOptions> . paralel döngü, tek bir iptal işlemi oluşturur <xref:System.OperationCanceledException> . Başka bir belirteç iptaline neden olursa, döngü bir <xref:System.AggregateException> InnerException olarak bir oluşturacak <xref:System.OperationCanceledException> şekilde oluşturur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri paralelliği](data-parallelism-task-parallel-library.md)
- [PLıNQ ve TPL 'deki lambda Ifadeleri](lambda-expressions-in-plinq-and-tpl.md)
