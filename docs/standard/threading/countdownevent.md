---
title: CountdownEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
ms.openlocfilehash: 628d6a96606117d447c61d01595d13dd4a957ce4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138117"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, bekleyen iş parçacıklarını belirli sayıda sinyalden sonra engelleyen bir eşitleme temel sayısıdır. <xref:System.Threading.CountdownEvent>, başka bir <xref:System.Threading.ManualResetEvent> veya <xref:System.Threading.ManualResetEventSlim> kullanmak zorunda olduğunuz ve olayı sinyalden önce bir değişkeni el ile azaltabileceği senaryolar için tasarlanmıştır. Örneğin, bir çatal/JOIN senaryosunda, yalnızca 5 numaralı sinyal sayısına sahip bir <xref:System.Threading.CountdownEvent> oluşturup iş parçacığı havuzunda beş iş öğesi başlatabilir ve her bir iş öğesi çağrısını tamamlandığında <xref:System.Threading.CountdownEvent.Signal%2A> sağlayabilirsiniz. <xref:System.Threading.CountdownEvent.Signal%2A> yapılan her bir çağrı, sinyal sayısını 1 azaltır. Ana iş parçacığında, <xref:System.Threading.CountdownEvent.Wait%2A> çağrısı, sinyal sayısı sıfır olana kadar engeller.  
  
> [!NOTE]
> Eski .NET Framework eşitleme API 'Leri ile etkileşim kurmak zorunda olmayan kod için, çatal birleştiren paralellik belirtme konusunda daha kolay bir yaklaşım için <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya <xref:System.Threading.Tasks.Parallel.Invoke%2A> metodunu kullanmayı düşünün.  
  
 <xref:System.Threading.CountdownEvent> şu ek özelliklere sahiptir:  
  
- Bekleme işlemi, iptal belirteçleri kullanılarak iptal edilebilir.  
  
- Örnek oluşturulduktan sonra sinyal sayısı arttırılabilirler.  
  
- Örnekler, <xref:System.Threading.CountdownEvent.Wait%2A> <xref:System.Threading.CountdownEvent.Reset%2A> yöntemi çağırarak geri alındıktan sonra yeniden kullanılabilir.  
  
- Örnekler, <xref:System.Threading.WaitHandle.WaitAll%2A>gibi diğer .NET Framework eşitleme API 'Leriyle tümleştirme için <xref:System.Threading.WaitHandle> sunar.  
  
## <a name="basic-usage"></a>Temel kullanım  
 Aşağıdaki örnek, <xref:System.Threading.ThreadPool> iş öğeleriyle <xref:System.Threading.CountdownEvent> nasıl kullanacağınızı gösterir.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>Iptal Ile CountdownEvent  
 Aşağıdaki örnek, bir iptal belirteci kullanarak <xref:System.Threading.CountdownEvent> bekleme işleminin nasıl iptal edildiğini gösterir. Temel model, .NET Framework 4 ' te tanıtılan Birleşik iptal için modeli izler. Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Bekleme işleminin sinyal veren iş parçacıklarını iptal etmediğini unutmayın. Genellikle, iptal, mantıksal bir işleme uygulanır ve bu, olayın ve bekleyen tüm iş öğelerinin de tamamlanmasını içerebilir. Bu örnekte, her iş öğesi, iptal isteğine yanıt verebilmesi için aynı iptal belirtecinin bir kopyasını geçti.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
