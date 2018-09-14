---
title: Paralel Programlama için Veri Yapıları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6453e9983086dcb5b97ec134db9d74160d7a47cf
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594339"
---
# <a name="data-structures-for-parallel-programming"></a>Paralel Programlama için Veri Yapıları
.NET Framework sürüm 4 paralel programlama eşzamanlı koleksiyon sınıfları, hafif eşitleme temellerine ve yavaş başlatma türlerine yönelik birtakım dahil olmak üzere, kullanışlı olan birkaç yeni türlerini tanıtır. Bu tür görev paralel kitaplığı ve PLINQ'da dahil olmak üzere birden çok iş parçacıklı uygulamanın kodlar ile kullanabilirsiniz.  
  
## <a name="concurrent-collection-classes"></a>Eşzamanlı koleksiyon sınıfları  
 Koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı sağlayan iş parçacığı ekleme ve kaldırma kilitleri mümkün olduğunda kaçının işlemleri ve kilitler olduğu gerekli hassas kilitleme kullanın. .NET Framework sürümleri 1.0 ve 2.0 içinde tanıtılan koleksiyonlarından farklı olarak eşzamanlı koleksiyon sınıfı öğelerini eriştiğinde kilitleri almak üzere kullanıcı kodunun gerektirmez. Eşzamanlı koleksiyon sınıflarını performansını önemli ölçüde türleri üzerinden gibi artırabilir <xref:System.Collections.ArrayList?displayProperty=nameWithType> ve <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (ile kullanıcı olarak uygulanan kilitleme) senaryolarında burada birden çok iş parçacığı ekleyin ve öğeleri bir koleksiyondan Kaldır.  
  
 Yeni eşzamanlı koleksiyon sınıfları aşağıdaki tabloda listelenmektedir:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Özellikleri uygulayan bir iş parçacığı güvenli koleksiyonları için sınırlama ve engelleme sağlar <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>. Hiçbir yuva yok veya koleksiyon tam ise, üretici iş parçacıkları engelleyin. Koleksiyonu boş ise tüketici iş parçacıkları engelleyin. Bu tür, engelleyici olmayan erişim Tüketicileri ve üreticileri tarafından da destekler. <xref:System.Collections.Concurrent.BlockingCollection%601> yedekleme deposu destekleyen herhangi bir koleksiyon sınıfının için sınırlama ve engelleme sağlamak veya bir temel sınıf olarak kullanılabilir <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Ölçeklenebilir sağlayan bir iş parçacığı açısından güvenli paketi uygulama ekleyin ve işlemleri Al.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Eş zamanlı ve ölçeklenebilir bir sözlük türü.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Bir eş zamanlı ve ölçeklenebilir FIFO sırası.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Bir eş zamanlı ve ölçeklenebilir LIFO yığını.|  
  
 Daha fazla bilgi için [iş parçacığı güvenli koleksiyonları](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Eşitleme temellerine  
 İçinde yeni eşitleme temellerine <xref:System.Threading?displayProperty=nameWithType> ad alanı etkinleştirme ayrıntılı eşzamanlılık ve daha hızlı performans eski çoklu iş parçacığı kodda bulunan pahalı kilitleme mekanizmaları önleyerek. Bazı yeni türlerini gibi <xref:System.Threading.Barrier?displayProperty=nameWithType> ve <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> hiçbir karşılıkları .NET Framework'ün daha önceki sürümlerde vardır.  
  
 Aşağıdaki tablo, yeni eşitleme türlerini listeler:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Birden çok iş parçacığı bir nokta, her görev gelişini işaret eder ve ardından bazı veya tüm görevleri gelmiş kadar engelleyin sağlayarak paralel algoritma üzerinde çalışmanıza olanak sağlar. Daha fazla bilgi için [engel](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Bir kolayca randevu mekanizması sağlayarak çatallanma ve birleşme senaryolarını basitleştirir. Daha fazla bilgi için [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Benzer şekilde bir eşitleme temel <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim> daha basit ancak yalnızca işlem içi iletişim için kullanılabilir. Daha fazla bilgi için [ManualResetEvent ve ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md).|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Aynı anda bir kaynağa erişmek için iş parçacığı sayısını veya bir kaynak havuzu sınırları eşitleme temel. Daha fazla bilgi için [semafor ve SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|İş parçacığı neden karşılıklı dışlama kilidini temel bir döngüde beklenecek kilit çalışıyor veya *döndürme*, bir süre önce kuantum sonuçlanmıyor. Burada kilidi beklemek kısa olması beklenir senaryolarda <xref:System.Threading.SpinLock> teklifler daha iyi performans kilitleme diğer formları daha. Daha fazla bilgi için [SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Döngü sayısı aşılırsa, belirtilen bir süre boyunca ve en sonunda döndürme küçük, basit bir tür iş parçacığı bir bekleme durumuna yerleştirin.  Daha fazla bilgi için [SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Daha fazla bilgi için bkz.:  
  
-   [Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [Nasıl yapılır: eş zamanlı görevleri bir engelle eşitleme](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Yavaş başlatma sınıfları  
 Gerekli kadar geç başlatma ile bir nesne için bellek ayrılmadı. Yavaş başlatma, nesne ayırmalarını eşit bir program ömrü yayarak performansını iyileştirebilir. Herhangi bir özel tür için yavaş başlatma türü sarmalama tarafından etkinleştirebilirsiniz <xref:System.Lazy%601>.  
  
 Yavaş başlatma türleri aşağıdaki tabloda listelenmektedir:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Basit, iş parçacığı açısından güvenli yavaş başlatma sağlar.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Gevşek başlatılan bir değer gevşek çağırma-başlatma işlevinin her bir iş parçacığı ile bir iş parçacığı başına temelinde sağlar.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Belirtilmesinin gerekmemesi ayrılmış, yavaş başlatma örneği ayırın statik yöntemler sağlar. Bunun yerine, bunlar bunlar erişilir hedefleri başlatıldığından emin olmak için başvurular kullanın.|  
  
 Daha fazla bilgi için [yavaş başlatma](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Toplama özel durumları  
 <xref:System.AggregateException?displayProperty=nameWithType> Türü, ayrı iş parçacığı üzerinde eşzamanlı olarak atılır ve bunları tek bir özel durum olarak katılan iş parçacığına geri dönüp birden çok özel durumları yakalamak için kullanılabilir. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> türleri ve PLINQ <xref:System.AggregateException> bu amaçla yaygın olarak. Daha fazla bilgi için [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) ve [nasıl yapılır: PLINQ sorgusunda özel durumları işlemek](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- <xref:System.Threading?displayProperty=nameWithType>  
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
