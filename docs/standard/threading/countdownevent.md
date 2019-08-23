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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac1f2283ad30499748511e6fed6d5ce98da7fd14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960101"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, bekleyen iş parçacıklarını belirli sayıda sinyalden sonra engelleyen bir eşitleme temel larıdır. <xref:System.Threading.CountdownEvent>, aksi takdirde bir <xref:System.Threading.ManualResetEvent> veya <xref:System.Threading.ManualResetEventSlim> kullanmanız gereken senaryolar için tasarlanmıştır ve olayı sinyalden önce bir değişkeni el ile azaltır. Örneğin, bir çatal/JOIN senaryosunda, yalnızca 5 numaralı sinyal sayısına sahip bir <xref:System.Threading.CountdownEvent> tane oluşturabilir ve sonra iş parçacığı havuzunda beş iş öğesi başlatabilir ve tamamlandığında her iş öğesi çağrısını <xref:System.Threading.CountdownEvent.Signal%2A> yapabilirsiniz. Her çağrı <xref:System.Threading.CountdownEvent.Signal%2A> , sinyal sayısını 1 ' i azaltır. Ana iş parçacığında, çağrısı <xref:System.Threading.CountdownEvent.Wait%2A> , sinyal sayısı sıfır olana kadar engeller.  
  
> [!NOTE]
> Eski .NET Framework eşitleme API 'leri ile etkileşim kurmak zorunda olmayan kod için, çatalı birleştiren paralellik ifade etmek <xref:System.Threading.Tasks.Parallel.Invoke%2A> için nesneleri veya yöntemi kullanmayı <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> düşünün.  
  
 <xref:System.Threading.CountdownEvent>Şu ek özelliklere sahiptir:  
  
- Bekleme işlemi, iptal belirteçleri kullanılarak iptal edilebilir.  
  
- Örnek oluşturulduktan sonra sinyal sayısı arttırılabilirler.  
  
- Örnekler, <xref:System.Threading.CountdownEvent.Wait%2A> <xref:System.Threading.CountdownEvent.Reset%2A> yöntemi çağırarak döndürülmeden sonra yeniden kullanılabilir.  
  
- Örnekler, gibi <xref:System.Threading.WaitHandle> diğer .NET Framework eşitleme API 'leri <xref:System.Threading.WaitHandle.WaitAll%2A>ile tümleştirme için sunar.  
  
## <a name="basic-usage"></a>Temel kullanım  
 Aşağıdaki örnek, <xref:System.Threading.CountdownEvent> ile <xref:System.Threading.ThreadPool> iş öğelerinin nasıl kullanılacağını göstermektedir.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>Iptal Ile CountdownEvent  
 Aşağıdaki örnek, bir iptal belirteci kullanılarak üzerinde <xref:System.Threading.CountdownEvent> bekleme işleminin nasıl iptal edildiğini gösterir. Temel model, .NET Framework 4 ' te tanıtılan Birleşik iptal için modeli izler. Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Bekleme işleminin sinyal veren iş parçacıklarını iptal etmediğini unutmayın. Genellikle, iptal, mantıksal bir işleme uygulanır ve bu, olayın ve bekleyen tüm iş öğelerinin de tamamlanmasını içerebilir. Bu örnekte, her iş öğesi, iptal isteğine yanıt verebilmesi için aynı iptal belirtecinin bir kopyasını geçti.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
