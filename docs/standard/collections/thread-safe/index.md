---
title: İş Parçacığı Koleksiyonları
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, overview
ms.assetid: 2e7ca21f-786c-4367-96be-0cf3f3dcc6bd
ms.openlocfilehash: 7af59cf0fdbe8d5c7d7d586b4b86992ae1dc7601
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290376"
---
# <a name="thread-safe-collections"></a>İş Parçacığı Koleksiyonları
.NET Framework 4, <xref:System.Collections.Concurrent?displayProperty=nameWithType> hem iş parçacığı güvenli hem de ölçeklenebilir olan birkaç koleksiyon sınıfını içeren ad alanını tanıtır. Birden çok iş parçacığı, Kullanıcı kodunda ek eşitlemeye gerek duymadan, bu koleksiyonlardan öğeleri güvenle ve etkili bir şekilde ekleyebilir veya kaldırabilir. Yeni kod yazdığınızda, birden çok iş parçacığının koleksiyona aynı anda yazılacağı her seferinde eşzamanlı koleksiyon sınıflarını kullanın. Yalnızca paylaşılan bir koleksiyondan okuyorsanız <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanındaki sınıfları kullanabilirsiniz. .NET Framework 1.1 veya önceki çalışma zamanı sürümünü hedeflemeniz gerekmedikçe 1.0 koleksiyon sınıflarını kullanmamanızı öneririz.  
  
## <a name="thread-synchronization-in-the-net-framework-10-and-20-collections"></a>.NET Framework 1.0 ve 2.0 Koleksiyonlarındaki İş Parçacığı Eşitlemesi  
 .NET Framework 1.0'da tanıtılan koleksiyonlar <xref:System.Collections?displayProperty=nameWithType> ad alanında bulunur. Sık kullanılan <xref:System.Collections.ArrayList> ve <xref:System.Collections.Hashtable> öğelerini içeren bu koleksiyonlar, koleksiyon etrafında bir iş parçacığı güvenlikli sarmalayıcıyı döndüren `Synchronized` özelliği ile biraz iş parçacığı güvenliği sağlar. Sarmalayıcı, her ekleme veya kaldırma işleminde tüm koleksiyonu kilitleyerek çalışır. Bu nedenle, koleksiyona erişmeye çalışan her bir iş parçacığının bir kilidi almak için kendi sırasını beklemesi gerekir. Bu ölçeklenebilir değildir ve büyük koleksiyonlar için önemli performans düşüşüne neden olabilir. Ayrıca tasarım, yarış durumlarına karşı tamamen korumalı değildir. Daha fazla bilgi için bkz. [genel koleksiyonlardaki eşitleme](https://docs.microsoft.com/archive/blogs/bclteam/synchronization-in-generic-collections-brian-grunkemeyer).  
  
 .NET Framework 2.0'da tanıtılan koleksiyon sınıfları <xref:System.Collections.Generic?displayProperty=nameWithType> ad alanında bulunur. Bunlar <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.Dictionary%602> ve benzerlerini içerir. Bu sınıflar, .NET Framework 1.0 sınıfları ile karşılaştırıldığında geliştirilmiş tür güvenliği ve performans sağlar. Ancak, .NET Framework 2.0 koleksiyon sınıfları herhangi bir iş parçacığı eşitlemesi sağlamaz; kullanıcı kodunun, öğeler aynı anda birden çok iş parçacığına eklendiğinde veya kaldırıldığında tüm eşitlemeyi sağlaması gerekir.  
  
 .NET Framework 2,0 koleksiyon sınıflarının yalnızca tür güvenliğini sağlamadıkları ve ayrıca .NET Framework 1,0 koleksiyonlarından daha verimli ve daha fazla iş parçacığı güvenliği sağladıkları için .NET Framework 4 ' te eşzamanlı koleksiyonlar sınıflarını öneririz.  
  
## <a name="fine-grained-locking-and-lock-free-mechanisms"></a>Hassas Kilitleme ve Kilitsiz Mekanizmalar  
 Bazı eşzamanlı koleksiyon türleri,,, ve gibi basit eşitleme mekanizmalarını <xref:System.Threading.SpinLock> ( <xref:System.Threading.SpinWait> <xref:System.Threading.SemaphoreSlim> <xref:System.Threading.CountdownEvent> .NET Framework 4 ' te yeni) kullanır. Bu eşitleme türleri genellikle, iş parçacığını doğru bekleme durumuna almadan önce kısa dönemler için *meşgul dönmesini* kullanır. Bekleme sürelerinin çok kısa olması beklendiğinde pahalı bir çekirdek dönüşümünü içeren dönme beklemeden hesaplama açısından çok daha ucuzdur. Dönme kullanan koleksiyon sınıfları için bu verimlilik, birden çok iş parçacığının yüksek bir hızda öğe ekleyip kaldırabildiği anlamına gelir. Dönme ve engelleme hakkında daha fazla bilgi için bkz. [SpinLock](../../threading/spinlock.md) ve [SpinWait](../../threading/spinwait.md).  
  
 <xref:System.Collections.Concurrent.ConcurrentQueue%601> ve <xref:System.Collections.Concurrent.ConcurrentStack%601> sınıfları kilitleri hiç kullanmaz. Bunun yerine, iş parçacığı güvenliğini sağlamak için <xref:System.Threading.Interlocked> işlemlerine dayanırlar.  
  
> [!NOTE]
> Eşzamanlı koleksiyon sınıfları <xref:System.Collections.ICollection> öğesini desteklediğinden, ilgisi olmasa bile <xref:System.Collections.ICollection.IsSynchronized%2A> ve <xref:System.Collections.ICollection.SyncRoot%2A> özellikleri için uygulama sağlarlar. `IsSynchronized` her zaman `false`'i döndürür ve `SyncRoot` her zaman `null` (Visual Basic'te `Nothing`) olarak ayarlıdır.  
  
 Aşağıdaki tablo, <xref:System.Collections.Concurrent?displayProperty=nameWithType> ad alanındaki koleksiyon türlerini listeler.  
  
|Tür|Description|  
|----------|-----------------|  
|<xref:System.Collections.Concurrent.BlockingCollection%601>|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601> öğesini uygulayan herhangi bir tür için sınırlama ve engelleme işlevleri sağlar. Daha fazla bilgi için bkz. [BlockingCollection genel bakış](blockingcollection-overview.md).|  
|<xref:System.Collections.Concurrent.ConcurrentDictionary%602>|Anahtar-değer çiftlerinin sözlüğünün iş parçacığı açısından güvenli uygulaması.|  
|<xref:System.Collections.Concurrent.ConcurrentQueue%601>|Bir FIFO (ilk giren ilk çıkar) sırasının iş parçacığı açısından güvenli uygulaması.|  
|<xref:System.Collections.Concurrent.ConcurrentStack%601>|Bir LIFO (son giren ilk çıkar) yığının iş parçacığı açısından güvenli uygulaması.|  
|<xref:System.Collections.Concurrent.ConcurrentBag%601>|Öğelerin sırasız koleksiyonunun iş parçacığı açısından güvenli uygulaması.|  
|<xref:System.Collections.Concurrent.IProducerConsumerCollection%601>|Bir türün `BlockingCollection` içinde kullanılabilmesi için uygulaması gereken ara birim.|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[BlockingCollection Genel Bakışı](blockingcollection-overview.md)|<xref:System.Collections.Concurrent.BlockingCollection%601> türü tarafından sağlanan işlevselliği açıklar.|  
|[Nasıl yapılır: Öğeleri Ekleme ve Bir ConcurrentDictionary'dan Alma](how-to-add-and-remove-items.md)|Bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> öğesine öğelerin nasıl ekleneceğini ve kaldırılacağını açıklar.|  
|[Nasıl yapılır: Öğeleri Tek Tek Ekleme ve Bir BlockingCollection'dan Alma](how-to-add-and-take-items.md)|Salt okunur numaralayıcı kullanmadan bir engelleme koleksiyonundan öğelerin nasıl eklenip alınacağını açıklar.|  
|[Nasıl yapılır: Koleksiyona Sınırlama ve Engelleme İşlevi Ekleme](how-to-add-bounding-and-blocking.md)|Bir <xref:System.Collections.Concurrent.IProducerConsumerCollection%601> koleksiyonu için herhangi bir koleksiyon sınıfının temel depolama mekanizması olarak nasıl kullanılacağını açıklar.|  
|[Nasıl yapılır: Bir BlockingCollection'daki Öğeleri Kaldırmak için ForEach Kullanma](how-to-use-foreach-to-remove.md)|Bir engelleme koleksiyondaki tüm öğeleri kaldırmak için `foreach` (Visual Basic'te `For Each`) öğesinin nasıl kullanılacağını açıklar.|  
|[Nasıl yapılır: Ardışık Düzende Engelleme Koleksiyonu Dizilerini Kullanma](how-to-use-arrays-of-blockingcollections.md)|Bir ardışık düzeni uygulamak için birden çok engelleme koleksiyonunun aynı anda nasıl kullanılacağını açıklar.|  
|[Nasıl yapılır: ConcurrentBag Kullanarak Nesne Havuzu Oluşturma](how-to-create-an-object-pool.md)|Sürekli yenilerini oluşturmak yerine, nesneleri yeniden kullanabileceğiniz senaryolarda performansı artırmak için eşzamanlı torbaların nasıl kullanılacağını gösterir.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>
