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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138117"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>belirli bir sayıda sinyal verildikten sonra bekleyen iş parçacığı engellerini unengelbir senkronizasyon ilkel. <xref:System.Threading.CountdownEvent>aksi takdirde olay sinyalönce bir <xref:System.Threading.ManualResetEvent> veya el <xref:System.Threading.ManualResetEventSlim> ile bir değişken kullanmak zorunda kalacak senaryolar için tasarlanmıştır. Örneğin, bir çatal/birleştirme senaryosunda, yalnızca sinyal <xref:System.Threading.CountdownEvent> sayısı 5 olan bir tane oluşturabilir ve iş parçacığı havuzunda beş <xref:System.Threading.CountdownEvent.Signal%2A> iş öğesi başlatabilir ve tamamlandığında her iş öğesi aramasını sağlayabilirsiniz. Her çağrı <xref:System.Threading.CountdownEvent.Signal%2A> sinyal sayısını 1'e erdirer. Ana iş parçacığında, <xref:System.Threading.CountdownEvent.Wait%2A> sinyal sayısı sıfır olana kadar çağrı engellenir.  
  
> [!NOTE]
> Eski .NET Framework senkronizasyon API'leri ile etkileşime geçmesi <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> gerekmeyen <xref:System.Threading.Tasks.Parallel.Invoke%2A> kod için, çatal birleştirme paralelliğini ifade etmek için nesneleri veya yöntemi kullanmayı düşünün.  
  
 <xref:System.Threading.CountdownEvent>şu ek özelliklere sahiptir:  
  
- Bekleme işlemi iptal belirteçleri kullanılarak iptal edilebilir.  
  
- Örnek oluşturulduktan sonra sinyal sayısı artımlı olabilir.  
  
- Örnekler, yöntemi arayarak <xref:System.Threading.CountdownEvent.Wait%2A> döndürüldikten sonra yeniden kullanılabilir. <xref:System.Threading.CountdownEvent.Reset%2A>  
  
- Örnekler gibi <xref:System.Threading.WaitHandle.WaitAll%2A> <xref:System.Threading.WaitHandle> diğer .NET Framework senkronizasyon API'leri ile entegrasyon için ortaya .  
  
## <a name="basic-usage"></a>Temel Kullanım  
 Aşağıdaki örnek, bir <xref:System.Threading.CountdownEvent> iş öğesinin nasıl kullanılacağını <xref:System.Threading.ThreadPool> gösterir.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>İptal Ile CountdownOlay  
 Aşağıdaki örnek, bir iptal belirteci kullanarak bekleme işleminin <xref:System.Threading.CountdownEvent> nasıl iptal edilebildiğini gösterir. Temel desen, .NET Framework 4'te tanıtılan birleşik iptal modelini izler. Daha fazla bilgi için Yönetilen [İş Parçacıklarında İptal'e](../../../docs/standard/threading/cancellation-in-managed-threads.md)bakın.  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Bekleme işleminin sinyal veren iş parçacıklarını iptal etmediğini unutmayın. Genellikle, iptal mantıksal bir işlem uygulanır ve bu olay yanı sıra bekleme eşitleme olduğu tüm iş öğeleri bekleme içerebilir. Bu örnekte, her iş öğesi, iptal isteğine yanıt verebilmek için aynı iptal belirteci nin bir kopyasına geçirilir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
