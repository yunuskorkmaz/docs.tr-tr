---
title: 'Nasıl yapılır: Bir Parallel.For veya ForEach döngüsünü iptal etme'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cdb6e059fb1c7001bbe4da60e2936b1ad40cc1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618087"
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Nasıl yapılır: Bir Parallel.For veya ForEach döngüsünü iptal etme
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemleri iptal belirteçlerini kullanımıyla iptal etmeyi destekler. Genel olarak, iptal etme hakkında daha fazla bilgi için bkz [iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md). Paralel bir döngüde sağladığınız <xref:System.Threading.CancellationToken> yöntemine <xref:System.Threading.Tasks.ParallelOptions> parametresi ve ardından paralel çağrıyı bir try-catch bloğu içinde alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir çağrı iptal etme gösterir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Aynı yaklaşımı uygulayabileceğiniz bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> çağırın.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 Sinyalleri iptal belirteci aynı ise belirteç, belirtilen <xref:System.Threading.Tasks.ParallelOptions> paralel bir döngüden tek bir durum oluşturur sonra örnek <xref:System.OperationCanceledException> iptal seçeneğiyle ilgili. Diğer bir belirteç iptali neden olursa, döngü oluşturur bir <xref:System.AggregateException> ile bir <xref:System.OperationCanceledException> olarak bir InnerException.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
