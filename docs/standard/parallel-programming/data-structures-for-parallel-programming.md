---
title: Paralel Programlama için Veri Yapıları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
ms.openlocfilehash: a2271feae78100940b4ecac3c42c9bfefa7e1769
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123144"
---
# <a name="data-structures-for-parallel-programming"></a>Paralel Programlama için Veri Yapıları
.NET Framework sürüm 4 ' te, bir dizi eşzamanlı koleksiyon sınıfı, hafif eşitleme temelleri ve yavaş başlatma türleri dahil olmak üzere, paralel programlamada yararlı olan çeşitli yeni türler tanıtılmaktadır. Bu türleri, paralel kitaplığı ve PLıNQ görevi dahil, çok iş parçacıklı uygulama kodu ile birlikte kullanabilirsiniz.  
  
## <a name="concurrent-collection-classes"></a>Eşzamanlı koleksiyon sınıfları  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanındaki koleksiyon sınıfları iş parçacığı güvenli ekleme ve kaldırma işlemleri sağlar ve bu işlemler, mümkün olan yerlerde kilitleri ortadan kaldırır ve kilitlerin gerekli olduğu hassas bir kilitleme kullanır. 1,0 ve 2,0 .NET Framework sürümlerinde tanıtılan koleksiyonların aksine, eşzamanlı bir koleksiyon sınıfı, öğelere eriştiğinde kullanıcı kodunun herhangi bir kilit geçirmesine gerek yoktur. Eşzamanlı koleksiyon sınıfları, birden çok iş parçacığının bir koleksiyondaki öğeleri eklemesi ve kaldırması için <xref:System.Collections.ArrayList?displayProperty=nameWithType> ve <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (Kullanıcı tarafından uygulanan kilitleme ile) gibi türlerin performansını önemli ölçüde iyileştirebilir.  
  
 Aşağıdaki tabloda, yeni eşzamanlı koleksiyon sınıfları listelenmektedir:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>uygulayan iş parçacığı güvenli koleksiyonlar için engelleme ve sınırlayıcı yetenekler sağlar. Üretici iş parçacıkları, kullanılabilir yuva yoksa veya koleksiyon doluysa engellenir. Koleksiyon boşsa, tüketici iş parçacıkları engeller. Bu tür Ayrıca, tüketiciler ve üreticileri tarafından engellenmeyen erişimi de destekler. <xref:System.Collections.Concurrent.BlockingCollection%601>, <xref:System.Collections.Generic.IEnumerable%601>destekleyen herhangi bir koleksiyon sınıfı için engelleme ve sınırlama sağlamak üzere bir temel sınıf veya yedekleme deposu olarak kullanılabilir.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Ölçeklenebilir ekleme ve Get işlemleri sağlayan iş parçacığı güvenli bir paket uygulamasıdır.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Eşzamanlı ve ölçeklenebilir sözlük türü.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Eşzamanlı ve ölçeklenebilir bir FıFO kuyruğu.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Eşzamanlı ve ölçeklenebilir bir LıFO yığını.|  
  
 Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonlar](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Eşitleme temelleri  
 <xref:System.Threading?displayProperty=nameWithType> ad alanındaki yeni eşitleme temelleri, eski çoklu iş parçacıklı kodda bulunan pahalı kilitleme mekanizmalarından kaçınarak hassas eşzamanlılık ve daha hızlı performans sağlar. <xref:System.Threading.Barrier?displayProperty=nameWithType> ve <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> gibi yeni türlerden bazıları .NET Framework önceki sürümlerinde hiçbir karşılıksız değildir.  
  
 Aşağıdaki tabloda yeni eşitleme türleri listelenmektedir:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Birden çok iş parçacığının paralel bir algoritma üzerinde çalışmasını, her görevin gelişini işaret edip bir miktar veya tüm görevler gelene kadar engellemesini sağlar. Daha fazla bilgi için bkz. [engeli](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Kolay bir buluşma mekanizması sağlayarak çatalını ve katılmayı basitleştirir. Daha fazla bilgi için bkz. [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>benzer bir eşitleme temel. <xref:System.Threading.ManualResetEventSlim> daha hafif, ancak yalnızca işlem içi iletişim için kullanılabilir.|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Bir kaynağa veya kaynak havuzuna eşzamanlı olarak erişebilen iş parçacığı sayısını sınırlayan bir eşitleme temel. Daha fazla bilgi için bkz. [semafor ve SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Kilidi almaya çalışan iş parçacığının, bir döngü veya döndürme için, bir süre içinde, bir süre boyunca, bir zaman için bir döngü veya *döndürme*için beklemesini sağlayan bir karşılıklı dışlama kilit temel türü. Kilit bekleme işleminin Short olması beklenildiği senaryolarda, <xref:System.Threading.SpinLock> diğer kilitleme biçimlerinden daha iyi performans sunar. Daha fazla bilgi için bkz. [SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Belirli bir süre için döngü uygulanacak küçük, hafif bir tür ve sonuç sayısı aşılırsa iş parçacığını bekleme durumuna yerleştirir.  Daha fazla bilgi için bkz. [SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Daha fazla bilgi için bkz.:  
  
- [Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
- [Nasıl yapılır: eş zamanlı işlemleri bir engel Ile eşitler](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Yavaş başlatma sınıfları  
 Yavaş başlatma sayesinde bir nesne için bellek, gerekli olana kadar ayrılmaz. Yavaş başlatma, nesne ayırmalarını bir programın kullanım ömrü boyunca eşit bir şekilde dağıtarak performansı iyileştirebilir. <xref:System.Lazy%601>türünü sarmalayarak, herhangi bir özel tür için yavaş başlatmayı etkinleştirebilirsiniz.  
  
 Aşağıdaki tabloda, yavaş başlatma türleri listelenmektedir:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Hafif, iş parçacığı açısından güvenli yavaş başlatma sağlar.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Her bir iş parçacığı geç-başlatma işlevini çağırarak, iş parçacığı başına temelinde geç tarafından başlatılan bir değer sağlar.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Adanmış, yavaş başlatma örneği ayırma gereksinimini ortadan kaldırmak için statik yöntemler sağlar. Bunun yerine, erişilmesi durumunda hedeflerin başlatılmış olduğundan emin olmak için başvuruları kullanırlar.|  
  
 Daha fazla bilgi için bkz. [yavaş başlatma](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Özel durumları topla  
 <xref:System.AggregateException?displayProperty=nameWithType> türü, ayrı iş parçacıklarında aynı anda oluşturulan birden çok özel durumu yakalamak ve bunları birleştirme iş parçacığına tek bir özel durum olarak döndürmek için kullanılabilir. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> ve <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> türleri ve PLıNQ kullanımı, bu amaçla yoğun olarak <xref:System.AggregateException>. Daha fazla bilgi için bkz. [özel durum işleme](../../../docs/standard/parallel-programming/exception-handling-task-parallel-library.md) ve [nasıl yapılır: PLINQ sorgusunda özel durumları işleme](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- <xref:System.Threading?displayProperty=nameWithType>
- [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
