---
title: Paralel Programlama için Veri Yapıları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
ms.openlocfilehash: f9c130b73044440f24b7b8bbebe9527490a165c1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288530"
---
# <a name="data-structures-for-parallel-programming"></a>Paralel Programlama için Veri Yapıları
.NET Framework sürüm 4 ' te, bir dizi eşzamanlı koleksiyon sınıfı, hafif eşitleme temelleri ve yavaş başlatma türleri dahil olmak üzere, paralel programlamada yararlı olan çeşitli yeni türler tanıtılmaktadır. Bu türleri, paralel kitaplığı ve PLıNQ görevi dahil, çok iş parçacıklı uygulama kodu ile birlikte kullanabilirsiniz.  
  
## <a name="concurrent-collection-classes"></a>Eşzamanlı koleksiyon sınıfları  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>Ad alanındaki koleksiyon sınıfları iş parçacığı güvenli ekleme ve kaldırma işlemleri sağlar ve bu işlemler, mümkün olan her yerde kilitleri önlemenize ve kilitlerin gerekli olduğu hassas bir kilit kullanılmasına neden olur. 1,0 ve 2,0 .NET Framework sürümlerinde tanıtılan koleksiyonların aksine, eşzamanlı bir koleksiyon sınıfı, öğelere eriştiğinde kullanıcı kodunun herhangi bir kilit geçirmesine gerek yoktur. Eşzamanlı koleksiyon sınıfları, <xref:System.Collections.ArrayList?displayProperty=nameWithType> <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> birden çok iş parçacığının bir koleksiyondaki öğeleri eklemesi ve kaldırması halinde (Kullanıcı tarafından uygulanan kilitleme ile) gibi türlerin performansını önemli ölçüde iyileştirebilir.  
  
 Aşağıdaki tabloda, yeni eşzamanlı koleksiyon sınıfları listelenmektedir:  
  
|Tür|Description|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|, Uygulayan iş parçacığı güvenli koleksiyonlar için engelleme ve sınırlayıcı yetenekler sağlar <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> . Üretici iş parçacıkları, kullanılabilir yuva yoksa veya koleksiyon doluysa engellenir. Koleksiyon boşsa, tüketici iş parçacıkları engeller. Bu tür Ayrıca, tüketiciler ve üreticileri tarafından engellenmeyen erişimi de destekler. <xref:System.Collections.Concurrent.BlockingCollection%601>, tarafından desteklenen herhangi bir koleksiyon sınıfı için engelleme ve sınırlama sağlamak üzere bir temel sınıf veya yedekleme deposu olarak kullanılabilir <xref:System.Collections.Generic.IEnumerable%601> .|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Ölçeklenebilir ekleme ve Get işlemleri sağlayan iş parçacığı güvenli bir paket uygulamasıdır.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Eşzamanlı ve ölçeklenebilir sözlük türü.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Eşzamanlı ve ölçeklenebilir bir FıFO kuyruğu.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Eşzamanlı ve ölçeklenebilir bir LıFO yığını.|  
  
 Daha fazla bilgi için bkz. [Iş parçacığı güvenli koleksiyonlar](../collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Eşitleme temelleri  
 Ad alanındaki yeni eşitleme temelleri, <xref:System.Threading?displayProperty=nameWithType> eski çoklu iş parçacıklı kodda bulunan pahalı kilitleme mekanizmalarından kaçınarak ayrıntılı eşzamanlılık ve daha hızlı performans sağlar. Ve gibi yeni türlerden bazıları <xref:System.Threading.Barrier?displayProperty=nameWithType> <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> .NET Framework önceki sürümlerinde hiçbir karşılık yoktur.  
  
 Aşağıdaki tabloda yeni eşitleme türleri listelenmektedir:  
  
|Tür|Description|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Birden çok iş parçacığının paralel bir algoritma üzerinde çalışmasını, her görevin gelişini işaret edip bir miktar veya tüm görevler gelene kadar engellemesini sağlar. Daha fazla bilgi için bkz. [engeli](../threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Kolay bir buluşma mekanizması sağlayarak çatalını ve katılmayı basitleştirir. Daha fazla bilgi için bkz. [CountdownEvent](../threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Şuna benzer bir eşitleme temel <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> . <xref:System.Threading.ManualResetEventSlim>daha açık ağırlıkdır, ancak yalnızca işlem içi iletişim için kullanılabilir.|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Bir kaynağa veya kaynak havuzuna eşzamanlı olarak erişebilen iş parçacığı sayısını sınırlayan bir eşitleme temel. Daha fazla bilgi için bkz. [semafor ve SemaphoreSlim](../threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|Kilidi almaya çalışan iş parçacığının, bir döngü veya döndürme için, bir süre içinde, bir süre boyunca, bir zaman için bir döngü veya *döndürme*için beklemesini sağlayan bir karşılıklı dışlama kilit temel türü. Kilidin bekleme işleminin kısa olması beklenildiği senaryolarda, <xref:System.Threading.SpinLock> diğer kilitleme biçimlerinden daha iyi performans sunar. Daha fazla bilgi için bkz. [SpinLock](../threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Belirli bir süre için döngü uygulanacak küçük, hafif bir tür ve sonuç sayısı aşılırsa iş parçacığını bekleme durumuna yerleştirir.  Daha fazla bilgi için bkz. [SpinWait](../threading/spinwait.md).|  
  
 Daha fazla bilgi için bkz.  
  
- [Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma](../threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
- [Nasıl yapılır: eş zamanlı işlemleri bir engel Ile eşitler](../threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Yavaş başlatma sınıfları  
 Yavaş başlatma sayesinde bir nesne için bellek, gerekli olana kadar ayrılmaz. Yavaş başlatma, nesne ayırmalarını bir programın kullanım ömrü boyunca eşit bir şekilde dağıtarak performansı iyileştirebilir. Türü sarmalayarak herhangi bir özel tür için yavaş başlatmayı etkinleştirebilirsiniz <xref:System.Lazy%601> .  
  
 Aşağıdaki tabloda, yavaş başlatma türleri listelenmektedir:  
  
|Tür|Description|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Hafif, iş parçacığı açısından güvenli yavaş başlatma sağlar.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Her bir iş parçacığı geç-başlatma işlevini çağırarak, iş parçacığı başına temelinde geç tarafından başlatılan bir değer sağlar.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Adanmış, yavaş başlatma örneği ayırma gereksinimini ortadan kaldırmak için statik yöntemler sağlar. Bunun yerine, erişilmesi durumunda hedeflerin başlatılmış olduğundan emin olmak için başvuruları kullanırlar.|  
  
 Daha fazla bilgi için bkz. [yavaş başlatma](../../framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Özel durumları topla  
 <xref:System.AggregateException?displayProperty=nameWithType>Tür, farklı iş parçacıklarında aynı anda oluşturulan birden fazla özel durumu yakalamak ve bunları birleştirme iş parçacığına tek bir özel durum olarak döndürmek için kullanılabilir. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>Ve <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> TÜRLERI ve PLINQ <xref:System.AggregateException> Bu amaçla yoğun bir şekilde kullanılır. Daha fazla bilgi için bkz. [özel durum işleme](exception-handling-task-parallel-library.md) ve [nasıl yapılır: PLINQ sorgusunda özel durumları işleme](how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- <xref:System.Threading?displayProperty=nameWithType>
- [Paralel programlama](index.md)
