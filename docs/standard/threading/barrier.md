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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138157"
---
# <a name="barrier"></a>Engel

<xref:System.Threading.Barrier?displayProperty=nameWithType>, birden çok iş parçacığının ( *katılımcılar*olarak bilinir) aşamalar halinde bir algoritmada eşzamanlı olarak çalışmasını sağlayan bir eşitleme temel masıdır. Her katılımcı, koddaki engel noktasına ulaşıncaya kadar yürütülür. Engel, bir iş aşamasının sonunu temsil eder. Bir katılımcı blobuna ulaştığında, tüm katılımcılar aynı engelye ulaşana kadar engeller. Tüm katılımcılar engelye ulaştıktan sonra, isteğe bağlı olarak bir aşama sonrası eylemi çağırabilirsiniz. Bu son aşama eylemi, diğer tüm iş parçacıkları hala engellenirken eylemleri tek bir iş parçacığı tarafından gerçekleştirmek için kullanılabilir. Eylem yürütüldükten sonra katılımcıların engeli kaldırılır.  
  
 Aşağıdaki kod parçacığında temel bir engel gösterilmektedir.  
  
 [!code-csharp[CDS_Barrier#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#02)]
 [!code-vb[CDS_Barrier#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#02)]  
  
 Tüm bir örnek için bkz. [nasıl yapılır: eş zamanlı işlemleri bir engel ile senkronize etme](how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="adding-and-removing-participants"></a>Katılımcıları ekleme ve kaldırma

 Bir <xref:System.Threading.Barrier> örneği oluşturduğunuzda, katılımcı sayısını belirtin. Ayrıca, istediğiniz zaman dinamik olarak katılımcı ekleyebilir veya kaldırabilirsiniz. Örneğin, bir katılımcı sorunun parçasını çözerse, sonucu saklayabilir, bu iş parçacığında yürütmeyi durdurabilir ve engelteki katılımcı sayısını azaltmak için <xref:System.Threading.Barrier.RemoveParticipant%2A?displayProperty=nameWithType> çağırabilirsiniz. <xref:System.Threading.Barrier.AddParticipant%2A?displayProperty=nameWithType>çağırarak bir katılımcı eklediğinizde, dönüş değeri, yeni katılımcının işini başlatmak için yararlı olabilecek geçerli aşama numarasını belirtir.  
  
## <a name="broken-barriers"></a>Bozuk engelleri

 Bir katılımcının engeli geçemediğinde kilitlenmeler meydana gelebilir. Bu kilitlenmeleri önlemek için <xref:System.Threading.Barrier.SignalAndWait%2A?displayProperty=nameWithType> yönteminin aşırı yüklerini kullanarak bir zaman aşımı süresi ve bir iptal belirteci belirtin. Bu aşırı yüklemeler, her katılımcının bir sonraki aşamaya devam etmeden önce denetlemesindeki bir Boole değeri döndürür.  
  
## <a name="post-phase-exceptions"></a>Son aşama özel durumları

 Aşama sonrası temsilci bir özel durum oluşturursa, daha sonra tüm katılımcılara yayılan bir <xref:System.Threading.BarrierPostPhaseException> nesnesine sarmalanır.  
  
## <a name="barrier-versus-continuewhenall"></a>Engel ve devam eden

 Engelleri, özellikle iş parçacıkları Döngülerde birden çok aşama gerçekleştirirken yararlı olur. Kodunuz yalnızca bir veya iki iş aşaması gerektiriyorsa, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nesneleri her türlü örtük birleşimde kullanıp kullanmayacağınızı göz önünde bulundurun:  
  
- <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.Invoke%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>  
  
- <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>  
  
 Daha fazla bilgi için bkz. [devamlılık görevlerini kullanarak görevleri zincirleme](../parallel-programming/chaining-tasks-by-using-continuation-tasks.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İş parçacığı nesneleri ve özellikleri](threading-objects-and-features.md)
- [Nasıl yapılır: eş zamanlı işlemleri bir engel ile senkronize etme](how-to-synchronize-concurrent-operations-with-a-barrier.md)
