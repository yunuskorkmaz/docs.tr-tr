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
ms.openlocfilehash: f98e2388cb31e62d974c8b0bae0bdf833f5963a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585366"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> belirli bir kaç kez eşitleme ilkel edildikten sonra bekleyen parçacıklarını engelini kaldırır işaret olur. <xref:System.Threading.CountdownEvent> Aksi takdirde sahip olduğunuz kullanılacak senaryoları için tasarlanan bir <xref:System.Threading.ManualResetEvent> veya <xref:System.Threading.ManualResetEventSlim> ve olay sinyal önce el ile bir değişken azaltma. Örneğin, bir çatalı/JOIN senaryosunda, yalnızca oluşturabileceğiniz bir <xref:System.Threading.CountdownEvent> 5 sinyal sayısını sahip ve ardından Başlat beş iş öğeleri iş parçacığı üzerinde havuz ve her iş öğesi çağrısı <xref:System.Threading.CountdownEvent.Signal%2A> tamamlandığında. Her çağrı <xref:System.Threading.CountdownEvent.Signal%2A> sinyal sayısı 1 ile azaltır. Çağrı ana iş parçacığı üzerinde <xref:System.Threading.CountdownEvent.Wait%2A> sinyal sayısı sıfır olana kadar engeller.  
  
> [!NOTE]
>  Eski .NET Framework eşitleme API'leri ile etkileşim kurmak zorunda değildir kodu kullanmayı <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri veya <xref:System.Threading.Tasks.Parallel.Invoke%2A> çatalı birleştirme paralellik ifade etmek için daha kolay bir yaklaşım için yöntem.  
  
 <xref:System.Threading.CountdownEvent> Bu ek özellikler vardır:  
  
-   Bekleme işlemini iptal belirteçleri kullanarak iptal edilebilir.  
  
-   Örneği oluşturulduktan sonra onun sinyal sayısı artar.  
  
-   Örneği yeniden kullanılabilir sonra <xref:System.Threading.CountdownEvent.Wait%2A> çağırarak döndürdü <xref:System.Threading.CountdownEvent.Reset%2A> yöntemi.  
  
-   Örnekleri kullanıma bir <xref:System.Threading.WaitHandle> diğer .NET Framework eşitleme API'leri ile tümleştirme gibi <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## <a name="basic-usage"></a>Temel kullanım  
 Aşağıdaki örnekte nasıl kullanılacağını gösteren bir <xref:System.Threading.CountdownEvent> ile <xref:System.Threading.ThreadPool> iş öğeleri.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>İptal etme ile CountdownEvent  
 Aşağıdaki örnek, üzerinde bekleme işlemini iptal etmek gösterilmiştir <xref:System.Threading.CountdownEvent> kullanarak bir iptal belirteci. Model sunulan birleşik iptali için temel deseni izler [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Daha fazla bilgi için bkz: [yönetilen iş parçacıklarında iptal](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Bekleme işlem sinyal iş parçacıkları iptal etmez unutmayın. Genellikle, mantıksal bir işlemi iptal uygulanır ve beklemeyi eşitleme tüm iş öğeleri yanı sıra olay üzerinde bekleyen içerebilir. İptal isteğine yanıt vermesi Bu örnekte, aynı iptal belirtecini bir kopyasını her iş öğesi geçirilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
