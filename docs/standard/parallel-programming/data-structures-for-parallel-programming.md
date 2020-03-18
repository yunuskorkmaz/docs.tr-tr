---
title: Paralel Programlama için Veri Yapıları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
ms.openlocfilehash: a2271feae78100940b4ecac3c42c9bfefa7e1769
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73123144"
---
# <a name="data-structures-for-parallel-programming"></a>Paralel Programlama için Veri Yapıları
.NET Framework sürüm 4, eşzamanlı toplama sınıfları kümesi, hafif eşitleme ilkelleri ve tembel başlatma türleri de dahil olmak üzere paralel programlamada yararlı olan birkaç yeni tür sunar. Görev Paralel Kitaplığı ve PLINQ dahil olmak üzere herhangi bir çok iş parçacığı uygulama kodu ile bu türleri kullanabilirsiniz.  
  
## <a name="concurrent-collection-classes"></a>Eşzamanlı Toplama Sınıfları  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType> Ad alanındaki koleksiyon sınıfları, mümkün olan her yerde kilitlenmeleri önleyen ve kilitlerin gerekli olduğu yerlerde ince taneli kilitleme kullanan iş parçacığı güvenli ekleme ve kaldırma işlemleri sağlar. .NET Framework sürümleri 1.0 ve 2.0'da tanıtılan koleksiyonlardan farklı olarak, eşzamanlı bir koleksiyon sınıfı öğelere erişirken kullanıcı kodunun kilit almasını gerektirmez. Eşzamanlı toplama sınıfları, birden çok iş <xref:System.Collections.ArrayList?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> parçacığının bir koleksiyondan öğe ekleyip kaldırdığı senaryolarda ve (kullanıcı tarafından uygulanan kilitleme yle) gibi türler üzerindeki performansı önemli ölçüde artırabilir.  
  
 Aşağıdaki tabloda yeni eşzamanlı toplama sınıfları listelenebvardır:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Uygulayan <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>iş parçacığı güvenli koleksiyonları için engelleme ve sınırlama yetenekleri sağlar. Yuva yoksa veya koleksiyon doluysa üretici iş parçacıkları bloke olur. Koleksiyon boşsa tüketici iş parçacıkları blok. Bu tür, tüketicilerin ve üreticilerin engellememe erişimini de destekler. <xref:System.Collections.Concurrent.BlockingCollection%601>destekleyen <xref:System.Collections.Generic.IEnumerable%601>herhangi bir toplama sınıfı için engelleme ve sınırlandırma sağlamak için bir taban sınıf veya destek deposu olarak kullanılabilir.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Ölçeklenebilir ekleme ve alma işlemleri sağlayan iş parçacığı güvenli bir torba uygulaması.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Eşzamanlı ve ölçeklenebilir sözlük türü.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Eşzamanlı ve ölçeklenebilir FIFO sırası.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Eşzamanlı ve ölçeklenebilir LIFO yığını.|  
  
 Daha fazla bilgi için [İş Parçacığı Güvenli Koleksiyonları'na](../../../docs/standard/collections/thread-safe/index.md)bakın.  
  
## <a name="synchronization-primitives"></a>Senkronizasyon İlkelleri  
 <xref:System.Threading?displayProperty=nameWithType> Ad alanındaki yeni eşitleme ilkelleri, eski çok iş parçacığı kodunda bulunan pahalı kilitleme mekanizmalarından kaçınarak ince taneli eşzamanlılık ve daha hızlı performans sağlar. .NET Framework'ün önceki <xref:System.Threading.Barrier?displayProperty=nameWithType> <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> sürümlerinde benzerleri yoktur ve benzerleri yoktur.  
  
 Aşağıdaki tabloda yeni eşitleme türleri listelenir:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Her görevin gelişini işaret edebileceği ve bazı veya tüm görevler gelene kadar engelleyebileceği bir nokta sağlayarak birden çok iş parçacığının bir algoritma üzerinde paralel olarak çalışmasını sağlar. Daha fazla bilgi için [Barrier'e](../../../docs/standard/threading/barrier.md)bakın.|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Kolay bir buluşma mekanizması sağlayarak çatalı basitleştirir ve senaryoları birleştirir. Daha fazla bilgi için [CountdownEvent'e](../../../docs/standard/threading/countdownevent.md)bakın.|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Bir senkronizasyon ilkel <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>benzer . <xref:System.Threading.ManualResetEventSlim>daha hafiftir, ancak yalnızca işlem içi iletişim için kullanılabilir.|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Aynı anda bir kaynağa veya kaynak havuzuna erişebilen iş parçacığı sayısını sınırlayan eşitleme ilkel. Daha fazla bilgi için [Semaphore ve SemaphoreSlim'e](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)bakınız.|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Bir döngü içinde beklemek için kilit elde etmek için çalışıyor iş parçacığı neden olan bir karşılıklı dışlama kilidi ilkel, ya da *spin*, kuantum verim önce bir süre için. Kilidin beklemesüresinin kısa olması beklenen senaryolarda, <xref:System.Threading.SpinLock> diğer kilitleme biçimlerine göre daha iyi performans sunar. Daha fazla bilgi için [Bkz. SpinLock.](../../../docs/standard/threading/spinlock.md)|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Belirli bir süre boyunca dönecek ve spin sayısı aşıldığında iş parçacığının bekleme durumuna getirilecek küçük, hafif bir tür.  Daha fazla bilgi için [SpinWait'e](../../../docs/standard/threading/spinwait.md)bakın.|  
  
 Daha fazla bilgi için bkz.  
  
- [Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
- [Nasıl?](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md)  
  
## <a name="lazy-initialization-classes"></a>Tembel Başlatma Sınıfları  
 Tembel başlatma ile, bir nesnenin belleği gerekli olunana kadar ayrılmaz. Tembel başlatma, nesne ayırmalarını bir programın ömrü boyunca eşit olarak yayarak performansı artırabilir. Türü sararak herhangi bir özel tür için <xref:System.Lazy%601>tembel başlatmayı etkinleştirebilirsiniz.  
  
 Aşağıdaki tabloda tembel başlatma türleri listelenir:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Hafif, iş parçacığı güvenli tembel başlatma sağlar.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Her iş parçacığı laily-başlatma işlevi çağıran, iş parçacığı başına bazda bir tembel-başharfdeğeri sağlar.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Özel, tembel-başlatma örneğini ayırma gereksinimini önleyen statik yöntemler sağlar. Bunun yerine, hedeflere erişildikçe başlatılan olduğundan emin olmak için başvuruları kullanırlar.|  
  
 Daha fazla bilgi [için, Lazy Initialization](../../../docs/framework/performance/lazy-initialization.md)bakın.  
  
## <a name="aggregate-exceptions"></a>Toplam Özel Durumlar  
 Tür, <xref:System.AggregateException?displayProperty=nameWithType> ayrı iş parçacıklarıüzerinde aynı anda atılan birden çok özel durum yakalamak ve bunları tek bir özel durum olarak birleştirme iş parçacığına döndürmek için kullanılabilir. Ve <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> türleri ve PLINQ bu amaç için yoğun olarak kullanın. <xref:System.AggregateException> Daha fazla bilgi için bkz: [Özel Durum İşleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) ve [Nasıl Yapılır: PLINQ Sorgusunda Özel Durumları İşleyin.](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- <xref:System.Threading?displayProperty=nameWithType>
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
