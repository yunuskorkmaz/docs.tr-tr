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
ms.openlocfilehash: 8ed1414ad377015400d9e126d924bf426fbc753d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277862"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, bekleyen iş parçacıklarını belirli sayıda sinyalden sonra engelleyen bir eşitleme temel larıdır. <xref:System.Threading.CountdownEvent>, aksi takdirde bir veya kullanmanız gereken senaryolar için tasarlanmıştır <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim> ve olayı sinyalden önce bir değişkeni el ile azaltır. Örneğin, bir çatal/JOIN senaryosunda, yalnızca <xref:System.Threading.CountdownEvent> 5 numaralı sinyal sayısına sahip bir tane oluşturabilir ve sonra iş parçacığı havuzunda beş iş öğesi başlatabilir ve tamamlandığında her iş öğesi çağrısını yapabilirsiniz <xref:System.Threading.CountdownEvent.Signal%2A> . Her çağrı <xref:System.Threading.CountdownEvent.Signal%2A> , sinyal sayısını 1 ' i azaltır. Ana iş parçacığında, çağrısı, <xref:System.Threading.CountdownEvent.Wait%2A> sinyal sayısı sıfır olana kadar engeller.  
  
> [!NOTE]
> Eski .NET Framework eşitleme API 'Leri ile etkileşim kurmak zorunda olmayan kod için, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel.Invoke%2A> çatalı birleştiren paralellik ifade etmek için nesneleri veya yöntemi kullanmayı düşünün.  
  
 <xref:System.Threading.CountdownEvent>Şu ek özelliklere sahiptir:  
  
- Bekleme işlemi, iptal belirteçleri kullanılarak iptal edilebilir.  
  
- Örnek oluşturulduktan sonra sinyal sayısı arttırılabilirler.  
  
- Örnekler <xref:System.Threading.CountdownEvent.Wait%2A> , yöntemi çağırarak döndürülmeden sonra yeniden kullanılabilir <xref:System.Threading.CountdownEvent.Reset%2A> .  
  
- Örnekler, gibi <xref:System.Threading.WaitHandle> diğer .NET Framework eşitleme API 'leri ile tümleştirme için sunar <xref:System.Threading.WaitHandle.WaitAll%2A> .  
  
## <a name="basic-usage"></a>Temel kullanım  
 Aşağıdaki örnek, <xref:System.Threading.CountdownEvent> ile iş öğelerinin nasıl kullanılacağını göstermektedir <xref:System.Threading.ThreadPool> .  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>Iptal Ile CountdownEvent  
 Aşağıdaki örnek, <xref:System.Threading.CountdownEvent> bir iptal belirteci kullanılarak üzerinde bekleme işleminin nasıl iptal edildiğini gösterir. Temel model, .NET Framework 4 ' te tanıtılan Birleşik iptal için modeli izler. Daha fazla bilgi için bkz. [yönetilen Iş parçacıklarında iptal](cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Bekleme işleminin sinyal veren iş parçacıklarını iptal etmediğini unutmayın. Genellikle, iptal, mantıksal bir işleme uygulanır ve bu, olayın ve bekleyen tüm iş öğelerinin de tamamlanmasını içerebilir. Bu örnekte, her iş öğesi, iptal isteğine yanıt verebilmesi için aynı iptal belirtecinin bir kopyasını geçti.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
