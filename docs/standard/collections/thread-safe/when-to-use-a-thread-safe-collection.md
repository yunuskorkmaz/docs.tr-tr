---
title: Bir İş Parçacığı Koleksiyonunun Ne Zaman Kullanılacağı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b224e758eb5b0e07c76f055f22bfe827789f07ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574845"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Bir İş Parçacığı Koleksiyonunun Ne Zaman Kullanılacağı
[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Desteklemek için özellikle tasarlanmış beş yeni koleksiyon türleri tanıtır çok iş parçacıklı ekleme ve kaldırma işlemleri. İş parçacığı güvenliği elde etmek için bu yeni tür verimli kilitleme ve kilidi serbest eşitleme mekanizmaları çeşitli kullanın. Eşitleme için bir işlem yükü ekler. Ek yük miktarı kullanılan eşitleme türü, gerçekleştirilen işlemleri türünü ve koleksiyon eşzamanlı olarak erişmeye çalıştığınız iş parçacığı sayısı gibi diğer faktörlere bağlıdır.  
  
 Bazı senaryolarda eşitleme ek yükü olduğu düşünülerek ve önemli ölçüde daha hızlı gerçekleştirmek ve bir dış kilidi ile korumalı iş parçacığı güvenli olmayan eşdeğer daha çok daha iyi ölçeklendirme çok iş parçacıklı türü etkinleştirir. Diğer senaryolarda yükü gerçekleştirmek ve aynı hakkında veya türü dışarıdan kilitli, iş parçacığı güvenli sürümünden daha da yavaş ölçeklemek iş parçacığı türü neden olabilir.  
  
 Aşağıdaki bölümler, ne zaman bir iş parçacığı koleksiyonunun bir kullanıcı tarafından sağlanan kilidi kendi okuma geçici olan iş parçacığı güvenli olmayan karşılığını karşı kullanın ve yazma işlemleri hakkında genel kılavuzluk sağlar. Performans birçok faktöre bağlı olarak farklılık gösterebileceğinden, yönerge özgü değildir ve her koşulda mutlaka geçerli değil. Performans çok önemliyse, daha sonra kullanmak için hangi koleksiyon türü belirlemek için en iyi temsilcisi bilgisayar yapılandırmalarını ve yükleri dayanarak performansı ölçmek için yoludur. Bu belge aşağıdaki terimler kullanılır:  
  
 *Saf üretici-tüketici senaryosu*  
 Belirli bir iş parçacığı ekleme veya öğeleri, ancak ikisini kaldırılıyor.  
  
 *Karma üretici-tüketici senaryosu*  
 Belirli bir iş parçacığı hem ekleme ve öğe kaldırma.  
  
 *Speedup*  
 Daha hızlı algoritmik performans aynı senaryoda başka bir türüne göre.  
  
 *Ölçeklenebilirlik*  
 Bilgisayarda çekirdek sayısı orantılıdır performansını artırma. Üzerinde iki çekirdeği makinelerinden ölçeklendirir bir algoritma üzerinde sekiz çekirdeği daha hızlı gerçekleştirir.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) vs. Queue(T)  
 Her öğe için işleme süresini olduğu çok küçük saf üretici-tüketici senaryolarda, (birkaç yönergeler), ardından <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> uygun performans avantajı üzerinden sunabileceği bir <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> bir dış kilit sahip. Bu senaryoda, <xref:System.Collections.Concurrent.ConcurrentQueue%601> tek bir adanmış iş parçacığı queuing ve tek bir adanmış iş parçacığı çıkarılması olduğunda en iyi şekilde çalışır. Bu kural, ardından zorlamaz varsa <xref:System.Collections.Generic.Queue%601> bile gerçekleştirebileceğiniz biraz daha hızlı <xref:System.Collections.Concurrent.ConcurrentQueue%601> birden çok çekirdeğe sahip bilgisayarlarda.  
  
 İşleme zamanı yaklaşık 500 FLOPS (kayan nokta işlemleri) veya daha sonra iki iş parçacığı kural uygulanmaz olduğunda <xref:System.Collections.Concurrent.ConcurrentQueue%601>, çok iyi ölçeklenebilirlik, daha sonra sahiptir. <xref:System.Collections.Generic.Queue%601> Bu senaryoda iyi ölçeklenmez.  
  
 İşlem süresi çok az olduğunda, üretici-tüketici senaryoları, karma bir <xref:System.Collections.Generic.Queue%601> bir dış olan kilit daha iyi ölçeklenir <xref:System.Collections.Concurrent.ConcurrentQueue%601> yapar. Ancak, işlem süresi olduğunda yaklaşık 500 FLOPS veya daha fazla sonra <xref:System.Collections.Concurrent.ConcurrentQueue%601> daha iyi ölçeklenir.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack vs. Yığın  
 Saf üretici-tüketici senaryolarda işleme süresi sonra çok küçük olduğunda <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> ve <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> bir dış olan kilit hakkında bir adanmış koymadan iş parçacığı ve tek bir adanmış pencerelerinin iş parçacığı ile aynı büyük olasılıkla gerçekleştirir. Ancak, iş parçacığı sayısı arttıkça sayısı olarak, her iki tür artan çakışma nedeniyle yavaşlayabilir ve <xref:System.Collections.Generic.Stack%601> gerçekleştirebileceğiniz daha iyi <xref:System.Collections.Concurrent.ConcurrentStack%601>. İşlem süresi yaklaşık 500 FLOPS olduğunda veya daha fazla ve ardından her iki türleri ölçekte aynı oranı hakkında.  
  
 Üretici-tüketici senaryoları, karma içinde <xref:System.Collections.Concurrent.ConcurrentStack%601> küçük ve büyük iş yükleri için daha hızlıdır.  
  
 Kullanımını <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> ve <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> erişim zamanları büyük ölçüde hızlandırabilir.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary vs. Sözlük  
 Genel olarak, kullanan bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> Burada, ekleme ve anahtarları veya aynı anda birden çok iş parçacığı değerleri güncelleştirme herhangi bir senaryoda. Sık güncelleştirmeler ve nispeten az okuma içeren senaryolarda <xref:System.Collections.Concurrent.ConcurrentDictionary%602> genellikle uygun avantajları sunar. Birçok okur ve çok sayıda güncelleştirme içeren senaryolarda <xref:System.Collections.Concurrent.ConcurrentDictionary%602> genellikle önemli ölçüde herhangi bir sayıda çekirdek olan bilgisayarlarda daha hızlıdır.  
  
 Sık güncelleştirmeler içeren senaryolarda eşzamanlılık derecesini artırabilir <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ve performansı daha fazla sayıda çekirdek olan bilgisayarlarda artırır olup olmadığını görmek için ölçebilirsiniz. Eşzamanlılık düzeyi değiştirirseniz, genel işlemlerini mümkün olduğunca kaçının.  
  
 Anahtar veya değer yalnızca okuyorsanız <xref:System.Collections.Generic.Dictionary%602> sözlük tüm iş parçacıkları tarafından değiştirilmeyen eşitleme gereklidir çünkü daha hızlıdır.  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 Saf üretici-tüketici senaryolarda <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> büyük olasılıkla daha diğer eş zamanlı koleksiyon türleri daha yavaş çalışır.  
  
 Üretici-tüketici senaryoları, karma içinde <xref:System.Collections.Concurrent.ConcurrentBag%601> genellikle çok daha hızlı ve daha ölçeklenebilir daha küçük ve büyük iş yükleri için başka bir eşzamanlı koleksiyon türü.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Sınırlama ve engelleme semantiği gerekli olduğunda <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> büyük olasılıkla herhangi bir özel uygulaması daha hızlı gerçekleştirir. Zengin iptal, numaralandırma ve özel durum işleme da destekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)  
 [Paralel Programlama](../../../../docs/standard/parallel-programming/index.md)
