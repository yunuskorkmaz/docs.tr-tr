---
title: Engel
ms.date: 09/14/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, Barrier
ms.assetid: 613a8bc7-6a28-4795-bd6c-1abd9050478f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cbbf7055a250ae7fa630097f3014a6420228fed3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088886"
---
# <a name="barrier"></a>Engel

A <xref:System.Threading.Barrier?displayProperty=nameWithType> birden çok iş parçacığını etkinleştiren eşitleme basit olduğunu (olarak bilinen *katılımcıları*) üzerinde bir algoritma aşamalarında eşzamanlı olarak çalışacak şekilde. Kodda engel noktası ulaşana kadar her katılımcı yürütür. Engel çalışmanın bir aşama sonunu temsil eder. Katılımcı engel ulaştığında, tüm katılımcılar aynı engele kadar engeller. Tüm katılımcıları engele sonra isteğe bağlı olarak bir aşama sonrası eylemi çağırabilirsiniz. Diğer tüm iş parçacıklarının hala engellenirken sonrası Bu aşama eylem eylemleri gerçekleştirmek için tek bir iş parçacığı tarafından kullanılabilir. Katılımcılar, tüm Eylem yürütüldükten sonra engellenmemektedir.  
  
 Aşağıdaki kod parçacığı bir engel temel deseni gösterir.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Tam bir örnek için bkz. [nasıl yapılır: eş zamanlı görevleri bir engelle eşitleme](how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Ekleme ve kaldırma katılımcıları

 Oluştururken bir <xref:System.Threading.Barrier> örneği, katılımcılar sayısını belirtin. Ayrıca, ekleyebilir veya katılımcıları dinamik olarak dilediğiniz zaman kaldırabilirsiniz. Örneğin, bir katılımcı kendi parçası sorunu çözer, iş parçacığı ve arama sonucu, Dur yürütülmesine depolayabilirsiniz <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> engel katılımcılarının sayısını azaltmak için. Eklediğinizde, bir katılımcı çağırarak <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>, dönüş değeri yeni katılımcı çalışmasını başlatmak için yararlı olabilecek geçerli aşama numarasını belirtir.  
  
## <a name="broken-barriers"></a>Bozuk engelleri

 Engel ulaşmak bir katılımcı başarısız olursa, kilitlenmeleri ortaya çıkabilir. Bu kilitlenmeleri önlemek için aşırı yüklemeleri kullanın. <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> bir zaman aşımı süresi ve bir iptal belirteci belirtmek için yöntemi. Bu aşırı yüklemeler dönüş her katılımcı önce denetleyebilen bir Boole değeri sonraki aşamaya devam eder.  
  
## <a name="post-phase-exceptions"></a>Son aşama özel durumları

 Sonrası aşaması temsilci bir özel durum oluşturursa, sarmalandıktan bir <xref:System.Threading.BarrierPostPhaseException> için tüm katılımcıları sonra yayılır nesnesidir.  
  
## <a name="barrier-versus-continuewhenall"></a>Engel ContinueWhenAll karşılaştırması

 İş parçacıklarını birden çok aşama Döngülerde gerçekleştirirken engelleri özellikle yararlı olur. Kodunuzu iş yalnızca bir veya iki aşamaya gerektiriyorsa, kullanıp kullanmayacağınızı düşünün <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> örtük birleşim, herhangi bir türden nesneler de dahil olmak üzere:  
  
-   <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
-   <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 Daha fazla bilgi için [kullanarak devamlılık görevleri zinciri görevleriyle](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)  
- [Nasıl yapılır: eş zamanlı görevleri bir engelle eşitleme](how-to-synchronize-concurrent-operations-with-a-barrier.md)
