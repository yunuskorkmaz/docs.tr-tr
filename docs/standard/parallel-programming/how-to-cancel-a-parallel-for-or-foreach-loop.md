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
ms.openlocfilehash: d29137127dd47844f8f08d3ac689cf2827d9efe2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288231"
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
