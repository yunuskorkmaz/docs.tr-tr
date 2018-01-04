---
title: Engel (.NET Framework)
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
helpviewer_keywords: synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 392e975f6bf566c2ba36290940eb0daee03f004f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="barrier-net-framework"></a>Engel (.NET Framework)
A *engel* birden çok iş parçacığı sağlayan bir kullanıcı tarafından tanımlanan eşitleme ilkel (olarak bilinen *katılımcıları*) aynı anda üzerinde bir algoritma aşamada çalışması için. Kodda engel noktası ulaşana kadar her katılımcı yürütür. Engeli iş bir aşamada sonunu temsil eder. Katılımcı engel ulaşırsa, tüm katılımcılar aynı engel ulaştınız kadar engeller. Tüm katılımcılar engel ulaştınız sonra sonrası aşaması eylem isteğe bağlı olarak çağırabilirsiniz. Diğer tüm iş parçacıklarının hala engellenirken sonrası Bu aşama eylemi eylemleri gerçekleştirmek için tek bir iş parçacığı tarafından kullanılabilir. Eylem yürütüldükten sonra katılımcıları tüm engellenmemiş.  
  
 Aşağıdaki kod parçacığını bir temel engel deseni gösterir.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Tam bir örnek için bkz: [nasıl yapılır: eşitleme eş zamanlı görevleri bir engelle ile](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Ekleme ve katılımcıları kaldırma  
 Oluştururken bir <xref:System.Threading.Barrier>, katılımcılar sayısını belirtin. Ayrıca ekleyebilir veya katılımcıları dinamik olarak dilediğiniz zaman kaldırabilirsiniz. Örneğin, bir katılımcı sorunun onun parçası çözer, iş parçacığı ve arama sonucu, Dur yürütülmesine depolayabilirsiniz <xref:System.Threading.Barrier.RemoveParticipant%2A> engel katılımcıları sayısını düşürmek için. Çağırarak katılımcı eklediğinizde <xref:System.Threading.Barrier.AddParticipant%2A>, dönüş değeri yeni katılımcı iş başlatmak için yararlı olabilecek geçerli aşama numarasını belirtir.  
  
## <a name="broken-barriers"></a>Bozuk engelleri  
 Kilitlenmeler bir katılımcı engel erişemeyen ortaya çıkabilir. Bu kilitlenmeler önlemek için aşırı kullanın <xref:System.Threading.Barrier.SignalAndWait%2A> yöntemi bir zaman aşımı süresi ve bir iptal belirteci belirtin. Bu aşırı dönüş her katılımcı önce kontrol edebilirsiniz bir Boole değeri sonraki aşamasına devam eder.  
  
## <a name="post-phase-exceptions"></a>Özel durumlar sonrası aşaması  
 Sonrası aşaması temsilci bir özel durum oluşturursa, paketlenir bir <xref:System.Threading.BarrierPostPhaseException> sonra tüm katılımcılar yayıldığı nesnesidir.  
  
## <a name="barrier-versus-continuewhenall"></a>Engel ContinueWhenAll karşılaştırması  
 İş parçacığı Döngülerde birden çok aşamaları gerçekleştirirken engelleri özellikle yararlı olur. Kodunuzu iş yalnızca bir veya iki aşamaları gerektiriyorsa, kullanıp kullanmayacağınızı düşünün <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> örtük birleştirme, her türlü nesneleriyle dahil olmak üzere:  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 Daha fazla bilgi için bkz: [zincirleme görevleri devamlılık görevlerini kullanarak tarafından](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
