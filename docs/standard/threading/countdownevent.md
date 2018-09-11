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
ms.openlocfilehash: 49b01fdd14d1adfe0480f93150ab6e996aa84dee
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44336857"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> sonra bekleyen iş parçacıklarının engellemesinin kaldırıldığı bir eşitleme temel öğesi bir belirli sayıda sinyal olur. <xref:System.Threading.CountdownEvent> içinde aksi takdirde kullanılacak senaryolarında için tasarlanmış bir <xref:System.Threading.ManualResetEvent> veya <xref:System.Threading.ManualResetEventSlim> ve el ile olay sinyal önce bir değişkeni azaltır. Örneğin, bir çatal/birleştir senaryosunda yalnızca oluşturabileceğiniz bir <xref:System.Threading.CountdownEvent> 5 sinyal sayısı olan ve sonra Başlangıç beş iş öğeleri iş parçacığı üzerinde havuz ve her iş öğesi arama sahip <xref:System.Threading.CountdownEvent.Signal%2A> tamamlandığında. Her çağrı <xref:System.Threading.CountdownEvent.Signal%2A> sinyal sayısı 1 ile azaltır. Ana iş parçacığı üzerinde çağrı <xref:System.Threading.CountdownEvent.Wait%2A> sinyal sayısı sıfır olana kadar engeller.  
  
> [!NOTE]
>  Eski .NET Framework eşitleme API'leri ile etkileşime geçmek için sahip olmayan kodu kullanmayı <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya <xref:System.Threading.Tasks.Parallel.Invoke%2A> çatal birleştirme paralellik ifade etme daha da kolay bir yaklaşım için yöntem.  
  
 <xref:System.Threading.CountdownEvent> Bu ek özellikler vardır:  
  
-   İptal belirteçleri kullanarak bekleme işlemi iptal edilebilir.  
  
-   Örneği oluşturulduktan sonra onun sinyal sayısının artırılması.  
  
-   Örneği yeniden kullanılabilir sonra <xref:System.Threading.CountdownEvent.Wait%2A> çağırarak döndürdü <xref:System.Threading.CountdownEvent.Reset%2A> yöntemi.  
  
-   Örnekleri kullanıma bir <xref:System.Threading.WaitHandle> diğer .NET Framework eşitleme API'ları ile tümleştirme gibi <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## <a name="basic-usage"></a>Temel kullanım  
 Aşağıdaki örnek nasıl kullanılacağını gösterir. bir <xref:System.Threading.CountdownEvent> ile <xref:System.Threading.ThreadPool> iş öğeleri.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent ile iptal etme  
 Aşağıdaki örnek, bekleme işlemi iptal işlemi gösterilmektedir <xref:System.Threading.CountdownEvent> kullanarak bir iptal belirteci. Sunulan birleşik iptal modeli temel düzeni izler [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Daha fazla bilgi için [yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Bekleme işlem sinyal iş parçacıkları iptal etmez unutmayın. Genellikle, iptal, mantıksal bir işlem için uygulanır ve beklemeyi eşitleme tüm iş öğelerini yanı sıra olay üzerinde bekleyen içerebilir. Bu örnekte, iptal isteğine yanıt vermesi her iş öğesi aynı iptal belirtecini bir kopyası geçirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
