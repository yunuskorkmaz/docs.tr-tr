---
title: "Paralel Programlama için Veri Yapıları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: data structures, multi-threading
ms.assetid: bdc82f2f-4754-45a1-a81e-fe2e9c30cef9
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f2da3e1ecfb9018adf7827aad6a569cd057c59eb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="data-structures-for-parallel-programming"></a>Paralel Programlama için Veri Yapıları
.NET Framework sürüm 4 paralel programlama, bir dizi eşzamanlı koleksiyon sınıfları, basit eşitleme temelleri ve türleri geç başlatma için de dahil olmak üzere kullanışlı olan birkaç yeni türleri tanıtır. Görev paralel kitaplığı ve PLINQ'da dahil olmak üzere tüm birden çok iş parçacıklı ile uygulama kodu, bu tür kullanabilirsiniz.  
  
## <a name="concurrent-collection-classes"></a>Eşzamanlı koleksiyon sınıfları  
 Koleksiyon sınıfları <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanı sağlayan iş parçacığı ekleme ve mümkün olduğunda kilitleri kaçının işlemleri kaldırma ve hassas kilitleri nerede gerekli kilitleme kullanın. .NET Framework sürüm 1.0 ve 2.0 sunulan koleksiyonlarından farklı olarak eşzamanlı koleksiyon sınıfı öğelerini eriştiğinde kilitleri yapılacak kullanıcı kodu gerektirmez. Eşzamanlı koleksiyon sınıfları performansı önemli ölçüde türleri üzerinden gibi iyileştirebilen <xref:System.Collections.ArrayList?displayProperty=nameWithType> ve <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> (ile kullanıcı uygulanan kilitleme) burada birden çok iş parçacığı ekleyin ve öğeleri koleksiyondan senaryolarda.  
  
 Aşağıdaki tabloda yeni eşzamanlı koleksiyon sınıfları listeler:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>|Engelleme ve yetenekleri uygulama iş parçacığı koleksiyonları için sınırlayıcı sağlar <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType>. Hiçbir yuva yok veya koleksiyon tam ise, üretici iş parçacığı engelleyin. Koleksiyon boş ise tüketici iş parçacığı engelleyin. Bu tür Tüketicileri ve üreticileri tarafından engellenmeyen erişimi de destekler. <xref:System.Collections.Concurrent.BlockingCollection%601>bir temel sınıf olarak kullanılabilir veya engelleme ve destekleyen herhangi bir koleksiyon sınıf için sınırlayıcı sağlamak için depolama yedekleme <xref:System.Collections.Generic.IEnumerable%601>.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>|Ölçeklenebilir sağlayan bir iş parçacığı paketi uygulaması eklemek ve işlemleri alın.|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>|Eş zamanlı ve ölçeklenebilir Sözlük türü.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>|Bir eş zamanlı ve ölçeklenebilir FIFO sırası.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>|Bir eş zamanlı ve ölçeklenebilir LIFO yığını.|  
  
 Daha fazla bilgi için bkz: [iş parçacığı koleksiyonları](../../../docs/standard/collections/thread-safe/index.md).  
  
## <a name="synchronization-primitives"></a>Eşitleme temelleri  
 İçinde yeni eşitleme Temelleri <xref:System.Threading?displayProperty=nameWithType> ad alanı hassas eşzamanlılık ve etkinleştirme daha hızlı performans eski çoklu iş parçacığı kullanımı kodda bulunan pahalı kilitleme mekanizmaları kaçınarak. Bazı yeni türleri gibi <xref:System.Threading.Barrier?displayProperty=nameWithType> ve <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> .NET Framework'ün önceki sürümlerde hiçbir ortaklarınıza sahip.  
  
 Aşağıdaki tablo, yeni eşitleme türlerini listeler:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Threading.Barrier?displayProperty=nameWithType>|Hangi her görev kendi varış sinyal ve bazı veya tüm görevleri gelmedi kadar sonra engellemek bir nokta sağlayarak bir algoritma paralel çalışmak birden çok iş parçacığı sağlar. Daha fazla bilgi için bkz: [engel](../../../docs/standard/threading/barrier.md).|  
|<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>|Bir kolay randevu mekanizması sağlayarak çatalı ve birleştirme senaryolarını basitleştirir. Daha fazla bilgi için bkz: [CountdownEvent](../../../docs/standard/threading/countdownevent.md).|  
|<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>|Benzer şekilde bir eşitleme temel <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>. <xref:System.Threading.ManualResetEventSlim>hafifletilmiş ancak yalnızca işlem içi iletişimi için kullanılabilir. Daha fazla bilgi için bkz: [ManualResetEvent ve ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md).|  
|<xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType>|Aynı anda bir kaynağa erişebilir iş parçacığı sayısını veya bir kaynak havuzu sınırlar bir eşitleme temel. Daha fazla bilgi için bkz: [semafor ve SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).|  
|<xref:System.Threading.SpinLock?displayProperty=nameWithType>|İş parçacığı neden bir karşılıklı dışlama kilit temel bir döngüde beklemek için kilit çalışıyor veya *döndürme*, kendi Zamanlayıcının sağlayan önce bir süre için. Burada kilidi bekle kısa, olması beklenir senaryolarda <xref:System.Threading.SpinLock> teklifleri daha iyi performans kilitleme başka biçimlerde daha. Daha fazla bilgi için bkz: [SpinLock](../../../docs/standard/threading/spinlock.md).|  
|<xref:System.Threading.SpinWait?displayProperty=nameWithType>|Döngü sayısı aşılırsa, belirli bir süredir ve sonunda Döndür küçük, basit bir tür iş parçacığı bir bekleme duruma.  Daha fazla bilgi için bkz: [SpinWait](../../../docs/standard/threading/spinwait.md).|  
  
 Daha fazla bilgi için bkz.:  
  
-   [Nasıl yapılır: Düşük Düzeyli Eşitleme için SpinLock Kullanma](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)  
  
-   [Nasıl yapılır: eş zamanlı görevleri bir engelle eşitleme](../../../docs/standard/threading/how-to-synchronize-concurrent-operations-with-a-barrier.md).  
  
## <a name="lazy-initialization-classes"></a>Geç Başlatma sınıfları  
 Gerekli kadar geç başlatma bir nesne için bellek ayrılmadı. Geç Başlatma nesne ayırmaları eşit bir program ömrü yayarak performansı artırabilir. Herhangi bir özel türü için geç başlatma türü kaydırma tarafından etkinleştirebilirsiniz <xref:System.Lazy%601>.  
  
 Aşağıdaki tabloda, geç başlatma türlerini listeler:  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Lazy%601?displayProperty=nameWithType>|Basit, iş parçacığı yavaş-başlatma sağlar.|  
|<xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType>|Gevşek başlatılan bir değer tek iş parçacığı başına temelinde gevşek çağırma-başlatma işlevinin her bir iş parçacığı ile sağlar.|  
|<xref:System.Threading.LazyInitializer?displayProperty=nameWithType>|Ayrılmış, geç başlatma örneği tahsis gereksinimini ortadan kaldırmak statik yöntemler sağlar. Bunun yerine, başvuruları bunlar erişilir hedefleri başlatılmadı emin olmak için kullanırlar.|  
  
 Daha fazla bilgi için bkz: [geç başlatma](../../../docs/framework/performance/lazy-initialization.md).  
  
## <a name="aggregate-exceptions"></a>Birleşik özel durumlar  
 <xref:System.AggregateException?displayProperty=nameWithType> Türü, aynı anda ayrı iş parçacıklarına oluşturulur ve tek bir özel durum olarak katılan iş parçacığına döndürün birden çok özel durumları yakalamak için kullanılabilir. <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> Ve <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> türleri ve PLINQ kullanmak <xref:System.AggregateException> kapsamlı olarak bu amaçla. Daha fazla bilgi için bkz: [NIB: nasıl yapılır: görevler tarafından özel durum işleme](http://msdn.microsoft.com/library/d6c47ec8-9de9-4880-beb3-ff19ae51565d) ve [nasıl yapılır: PLINQ sorgusunda özel durumları işlemek](../../../docs/standard/parallel-programming/how-to-handle-exceptions-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Threading?displayProperty=nameWithType>  
 [Paralel Programlama](../../../docs/standard/parallel-programming/index.md)
