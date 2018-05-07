---
title: İş Parçacığı Koleksiyonları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, overview
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7e0d5e53b255ab59eabace01e69784d88aec8aca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="thread-safe-collections"></a>İş Parçacığı Koleksiyonları
[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)], iş parçacığı açısından güvenli ve ölçeklenebilir birkaç koleksiyon sınıfı içeren <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanını tanıtır. Birden çok iş parçacığı güvenli bir şekilde ve verimli bir şekilde eklemek veya kullanıcı kodu ek eşitleme gerek kalmadan bu koleksiyonlardan öğeleri kaldırın. Yeni kod yazdığınızda, koleksiyon birden çok iş parçacığına aynı anda yazdığında eşzamanlı koleksiyon sınıflarını kullanın. Yalnızca paylaşılan bir koleksiyondan okuyorsanız <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki sınıfları kullanabilirsiniz. .NET Framework 1.1 veya önceki çalışma zamanı sürümünü hedeflemeniz gerekmedikçe 1.0 koleksiyon sınıflarını kullanmamanızı öneririz.  
  
## <a name="thread-synchronization-in-the-net-framework-10-and-20-collections"></a>.NET Framework 1.0 ve 2.0 Koleksiyonlarındaki İş Parçacığı Eşitlemesi  
 .NET Framework 1.0'da tanıtılan koleksiyonlar <xref:System.Collections?displayProperty=nameWithType> ad alanında bulunur. Sık kullanılan <xref:System.Collections.ArrayList> ve <xref:System.Collections.Hashtable> öğelerini içeren bu koleksiyonlar, koleksiyon etrafında bir iş parçacığı güvenlikli sarmalayıcıyı döndüren `Synchronized` özelliği ile biraz iş parçacığı güvenliği sağlar. Sarmalayıcı, her ekleme veya kaldırma işleminde tüm koleksiyonu kilitleyerek çalışır. Bu nedenle, koleksiyona erişmeye çalışan her bir iş parçacığının bir kilidi almak için kendi sırasını beklemesi gerekir. Bu ölçeklenebilir değildir ve büyük koleksiyonlar için önemli performans düşüşüne neden olabilir. Ayrıca tasarım, yarış durumlarına karşı tamamen korumalı değildir. Daha fazla bilgi için bkz: [genel koleksiyonlar eşitleme](https://blogs.msdn.microsoft.com/bclteam/2005/03/15/synchronization-in-generic-collections-brian-grunkemeyer/).  
  
 .NET Framework 2.0'da tanıtılan koleksiyon sınıfları <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanında bulunur. Bunlar <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602> ve benzerlerini içerir. Bu sınıflar, .NET Framework 1.0 sınıfları ile karşılaştırıldığında geliştirilmiş tür güvenliği ve performans sağlar. Ancak, .NET Framework 2.0 koleksiyon sınıfları herhangi bir iş parçacığı eşitlemesi sağlamaz; kullanıcı kodunun, öğeler aynı anda birden çok iş parçacığına eklendiğinde veya kaldırıldığında tüm eşitlemeyi sağlaması gerekir.  
  
 Eşzamanlı koleksiyonları sınıflarda öneririz [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] yalnızca .NET Framework 2.0 koleksiyon sınıflarının tür güvenliği ancak daha da daha etkili ve daha kapsamlı iş parçacığı güvenliği sağladıkları için [!INCLUDE[net_v10_short](../../../../includes/net-v10-short-md.md)] koleksiyonları sağlar.  
  
## <a name="fine-grained-locking-and-lock-free-mechanisms"></a>Hassas Kilitleme ve Kilitsiz Mekanizmalar  
 Bazı eşzamanlı koleksiyon türleri <xref:System.Threading.SpinLock>'da yeni olan <xref:System.Threading.SpinWait>, <xref:System.Threading.SemaphoreSlim>, <xref:System.Threading.CountdownEvent> ve [!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] gibi hafif eşitleme mekanizmalarını kullanır. Bu eşitleme türleri genellikle kullanmasına *meşgul dönen* true bekleme durumuna iş parçacığı koyarlar önce kısa bir süreliğine. Bekleme sürelerinin çok kısa olması beklendiğinde pahalı bir çekirdek dönüşümünü içeren dönme beklemeden hesaplama açısından çok daha ucuzdur. Dönme kullanan koleksiyon sınıfları için bu verimlilik, birden çok iş parçacığının yüksek bir hızda öğe ekleyip kaldırabildiği anlamına gelir. Dönen engelleme karşılaştırması hakkında daha fazla bilgi için bkz: [SpinLock](../../../../docs/standard/threading/spinlock.md) ve [SpinWait](../../../../docs/standard/threading/spinwait.md).  
  
 <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Concurrent.ConcurrentStack%601> sınıfları kilitleri hiç kullanmaz. Bunun yerine, iş parçacığı güvenliğini sağlamak için <xref:System.Threading.Interlocked> işlemlerine dayanırlar.  
  
> [!NOTE]
>  Eşzamanlı koleksiyon sınıfları <xref:System.Collections.ICollection> öğesini desteklediğinden, ilgisi olmasa bile <xref:System.Collections.ICollection.IsSynchronized%2A> ve <xref:System.Collections.ICollection.SyncRoot%2A> özellikleri için uygulama sağlarlar. `IsSynchronized` her zaman `false`'i döndürür ve `SyncRoot` her zaman `null` (Visual Basic'te `Nothing`) olarak ayarlıdır.  
  
 Aşağıdaki tablo, <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanındaki koleksiyon türlerini listeler.  
  
|Tür|Açıklama|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601> öğesini uygulayan herhangi bir tür için sınırlama ve engelleme işlevleri sağlar. Daha fazla bilgi için bkz: [BlockingCollection genel bakışı](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|Anahtar-değer çiftlerinin sözlüğünün iş parçacığı açısından güvenli uygulaması.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|Bir FIFO (ilk giren ilk çıkar) sırasının iş parçacığı açısından güvenli uygulaması.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|Bir LIFO (son giren ilk çıkar) yığının iş parçacığı açısından güvenli uygulaması.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|Öğelerin sırasız koleksiyonunun iş parçacığı açısından güvenli uygulaması.|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|Bir türün `BlockingCollection` içinde kullanılabilmesi için uygulaması gereken ara birim.|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[BlockingCollection’a Genel Bakış](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md)|<xref:System.Collections.Concurrent.BlockingCollection%601> türü tarafından sağlanan işlevselliği açıklar.|  
|[Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'den Alma](../../../../docs/standard/collections/thread-safe/how-to-add-and-remove-items.md)|Bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> öğesine öğelerin nasıl ekleneceğini ve kaldırılacağını açıklar.|  
|[Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan Alma](../../../../docs/standard/collections/thread-safe/how-to-add-and-take-items.md)|Salt okunur numaralayıcı kullanmadan bir engelleme koleksiyonundan öğelerin nasıl eklenip alınacağını açıklar.|  
|[Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme](../../../../docs/standard/collections/thread-safe/how-to-add-bounding-and-blocking.md)|Bir <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> koleksiyonu için herhangi bir koleksiyon sınıfının temel depolama mekanizması olarak nasıl kullanılacağını açıklar.|  
|[Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma](../../../../docs/standard/collections/thread-safe/how-to-use-foreach-to-remove.md)|Bir engelleme koleksiyondaki tüm öğeleri kaldırmak için `foreach` (Visual Basic'te `For Each`) öğesinin nasıl kullanılacağını açıklar.|  
|[Nasıl yapılır: İşlem Hattında Engelleme Koleksiyonu Dizilerini Kullanma](../../../../docs/standard/collections/thread-safe/how-to-use-arrays-of-blockingcollections.md)|Bir ardışık düzeni uygulamak için birden çok engelleme koleksiyonunun aynı anda nasıl kullanılacağını açıklar.|  
|[Nasıl yapılır: ConcurrentBag Kullanarak Nesne Havuzu Oluşturma](../../../../docs/standard/collections/thread-safe/how-to-create-an-object-pool.md)|Sürekli yenilerini oluşturmak yerine, nesneleri yeniden kullanabileceğiniz senaryolarda performansı artırmak için eşzamanlı torbaların nasıl kullanılacağını gösterir.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>
