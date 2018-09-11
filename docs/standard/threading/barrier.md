---
title: Engel (.NET Framework)
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 385e370f205851630f809b285a93c2609220efeb
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274775"
---
# <a name="barrier-net-framework"></a>Engel (.NET Framework)
A *engel* birden çok iş parçacığı sağlayan bir kullanıcı tanımlı eşitleme ilkel (olarak bilinen *katılımcıları*) üzerinde bir algoritma aşamalarında eşzamanlı olarak çalışacak şekilde. Kodda engel noktası ulaşana kadar her katılımcı yürütür. Engel çalışmanın bir aşama sonunu temsil eder. Katılımcı engel ulaştığında, tüm katılımcılar aynı engele kadar engeller. Tüm katılımcıları engele sonra isteğe bağlı olarak bir aşama sonrası eylemi çağırabilirsiniz. Diğer tüm iş parçacıklarının hala engellenirken sonrası Bu aşama eylem eylemleri gerçekleştirmek için tek bir iş parçacığı tarafından kullanılabilir. Katılımcılar, tüm Eylem yürütüldükten sonra engellenmemektedir.  
  
 Aşağıdaki kod parçacığı bir engel temel deseni gösterir.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Tam bir örnek için bkz. [nasıl yapılır: eş zamanlı görevleri bir engel ile eşitleme](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Ekleme ve kaldırma katılımcıları  
 Oluştururken bir <xref:System.Threading.Barrier>, katılımcılar sayısını belirtin. Ayrıca, ekleyebilir veya katılımcıları dinamik olarak dilediğiniz zaman kaldırabilirsiniz. Örneğin, bir katılımcı kendi parçası sorunu çözer, iş parçacığı ve arama sonucu, Dur yürütülmesine depolayabilirsiniz <xref:System.Threading.Barrier.RemoveParticipant%2A> engel katılımcılarının sayısını azaltmak için. Eklediğinizde, bir katılımcı çağırarak <xref:System.Threading.Barrier.AddParticipant%2A>, dönüş değeri yeni katılımcı çalışmasını başlatmak için yararlı olabilecek geçerli aşama numarasını belirtir.  
  
## <a name="broken-barriers"></a>Bozuk engelleri  
 Engel ulaşmak bir katılımcı başarısız olursa, kilitlenmeleri ortaya çıkabilir. Bu kilitlenmeleri önlemek için aşırı yüklemeleri kullanın. <xref:System.Threading.Barrier.SignalAndWait%2A> bir zaman aşımı süresi ve bir iptal belirteci belirtmek için yöntemi. Bu aşırı yüklemeler dönüş her katılımcı önce denetleyebilen bir Boole değeri sonraki aşamaya devam eder.  
  
## <a name="post-phase-exceptions"></a>Son aşama özel durumları  
 Sonrası aşaması temsilci bir özel durum oluşturursa, sarmalandıktan bir <xref:System.Threading.BarrierPostPhaseException> için tüm katılımcıları sonra yayılır nesnesidir.  
  
## <a name="barrier-versus-continuewhenall"></a>Engel ContinueWhenAll karşılaştırması  
 İş parçacıklarını birden çok aşama Döngülerde gerçekleştirirken engelleri özellikle yararlı olur. Kodunuzu iş yalnızca bir veya iki aşamaya gerektiriyorsa, kullanıp kullanmayacağınızı düşünün <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> örtük birleşim, herhangi bir türden nesneler de dahil olmak üzere:  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A>  
  
 Daha fazla bilgi için [kullanarak devamlılık görevleri zinciri görevleriyle](../../../docs/standard/parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş Parçacığı Nesneleri ve Özellikleri](../../../docs/standard/threading/threading-objects-and-features.md)  
- [Nasıl yapılır: Eş Zamanlı Görevleri bir Engelle Eşitleme](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)
