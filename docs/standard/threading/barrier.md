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
ms.openlocfilehash: 5aa34f7f39f4b9b626bea29372cf984f3cefb361
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138157"
---
# <a name="barrier"></a>Engel

A, <xref:System.Threading.Barrier?displayProperty=nameWithType> birden çok iş parçacığının *(katılımcılar*olarak bilinir) aşamalar halinde bir algoritma üzerinde aynı anda çalışmasını sağlayan bir eşitleme ilkelidir. Her katılımcı, koddaki bariyer noktasına ulaşana kadar yürütür. Bariyer, bir çalışma aşamasının sonunu temsil eder. Bir katılımcı bariyere ulaştığında, tüm katılımcılar aynı bariyere ulaşana kadar engeller. Tüm katılımcılar bariyere ulaştıktan sonra, isteğe bağlı olarak aşamalı bir eylem başlatabilirsiniz. Bu aşama sonrası eylem, diğer tüm iş parçacıkları hala engellenirken eylemleri tek bir iş parçacığı tarafından gerçekleştirmek için kullanılabilir. Eylem yürütüldükten sonra katılımcıların tümü engeli kaldırılır.  
  
 Aşağıdaki kod parçacığı temel bir engel deseni gösterir.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Tam bir örnek için [bkz: Eşzamanlı işlemleri Bir Bariyerle eşitleme.](how-to-synchronize-concurrent-operations-with-a-barrier.md)  
  
## <a name="adding-and-removing-participants"></a>Katılımcıların eklenmesi ve kaldırılması

 Bir <xref:System.Threading.Barrier> örnek oluşturduğunuzda, katılımcı sayısını belirtin. Ayrıca, katılımcıları istediğiniz zaman dinamik olarak ekleyebilir veya kaldırabilirsiniz. Örneğin, bir katılımcı sorunun kendi bölümünü çözerse, sonucu depolayabilir, yürütmeyi <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> bu iş parçacığıüzerinde durdurabilir ve engeldeki katılımcı sayısını azat etmeye çağırabilirsiniz. Bir katılımcıyı arayarak <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>eklediğinizde, iade değeri geçerli faz numarasını belirtir ve bu da yeni katılımcının çalışmasını başlatmada yararlı olabilir.  
  
## <a name="broken-barriers"></a>Kırık bariyerler

 Bir katılımcı bariyere ulaşamazsa kilitlenmeler oluşabilir. Bu kilitlenmeleri önlemek için, bir <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> zaman çıkış süresi ve iptal belirteci belirtmek için yöntemin aşırı yüklerini kullanın. Bu aşırı yüklemeler, her katılımcının bir sonraki aşamaya geçmeden önce kontrol edebileceği bir Boolean değerini döndürer.  
  
## <a name="post-phase-exceptions"></a>Aşama sonrası özel durumlar

 Aşama sonrası temsilci bir özel durum atarsa, daha <xref:System.Threading.BarrierPostPhaseException> sonra tüm katılımcılara yayılan bir nesneye sarılır.  
  
## <a name="barrier-versus-continuewhenall"></a>Bariyer karşı ContinueWhenAll

 İş parçacıkları döngüler halinde birden çok aşama gerçekleştirirken engeller özellikle yararlıdır. Kodunuz yalnızca bir veya iki çalışma aşaması gerektiriyorsa, nesnelerde örtük birleştirme ile birlikte kullanılıp kullanılmayacağınız <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ı göz önünde bulundurun:  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 Daha fazla bilgi için, [Devam Görevlerini Kullanarak Görevleri Zincirleme'ye](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [Nasıl: bir Bariyer ile eşzamanlı işlemleri senkronize](how-to-synchronize-concurrent-operations-with-a-barrier.md)
