---
title: "Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel foreach loop, how to cancel
- parallel for loops, how to cancel
ms.assetid: 9d19b591-ea95-4418-8ea7-b6266af9905b
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e3d2ba6776a46573599e581cbfdeb62d181b81e0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-cancel-a-parallelfor-or-foreach-loop"></a>Nasıl yapılır: Bir Parallel.For veya ForEach Döngüsünü İptal Etme
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> yöntemlerini desteklemek iptal iptal belirteçlerini kullanımı ile. Genel olarak, iptal hakkında daha fazla bilgi için bkz [iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md). Paralel bir döngüden sağladığınız <xref:System.Threading.CancellationToken> yöntemine <xref:System.Threading.Tasks.ParallelOptions> parametre ve bir try-catch bloğu içinde paralel çağrısı içine alın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek bir çağrı iptal etme gösterir <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>. Aynı yaklaşımı uygulayabilirsiniz bir <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> çağırın.  
  
 [!code-csharp[TPL_Parallel#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallel_cancel.cs#29)]
 [!code-vb[TPL_Parallel#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/cancelloop.vb#29)]  
  
 İptal sinyalleri belirteci aynı ise belirteç, belirtilen <xref:System.Threading.Tasks.ParallelOptions> paralel döngü tek bir özel durum oluşturacak sonra örnek <xref:System.OperationCanceledException> iptal üzerinde. Diğer bir belirteci iptal neden olursa, döngü özel durum oluşturacak bir <xref:System.AggregateException> ile bir <xref:System.OperationCanceledException> bir InnerException olarak.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Paralelliği](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [PLINQ ve TPL'deki Lambda İfadeleri](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
