---
title: Bir İş Parçacığı Koleksiyonunun Ne Zaman Kullanılacağı
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, when to upgrade
ms.assetid: a9babe97-e457-4ff3-b528-a1bc940d5320
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eefa1b52907525059b3403e7eb20542d3b5a5c73
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2018
ms.locfileid: "48245172"
---
# <a name="when-to-use-a-thread-safe-collection"></a>Bir İş Parçacığı Koleksiyonunun Ne Zaman Kullanılacağı
[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] Desteklemek için özel olarak tasarlanan beş yeni koleksiyon türlerini tanıtır çok iş parçacıklı ekleme ve kaldırma işlemleri. İş parçacığı güvenliği sağlamak için bu yeni türleri çeşitli verimli kilitleme ve kilitsiz eşitleme mekanizmaları kullanın. Eşitleme için bir işlem yükü ekler. Ek yük miktarı kullanılan eşitleme türü ve gerçekleştirilen işlemleri türünü eşzamanlı koleksiyon erişmeye çalıştığınız iş parçacığı sayısı gibi diğer faktörlere bağlıdır.  
  
 Bazı senaryolarda, eşitleme ek yükü göz ardı edilebilir ve çok iş parçacıklı türü önemli ölçüde daha hızlı gerçekleştirin ve dış bir kilit tarafından Korumalı iş parçacığı güvenli olmayan karşılığını daha çok daha iyi ölçeklendirme sağlar. Diğer senaryolarda, yükü gerçekleştirmek ve aynı hakkında veya türün dışarıdan kilitli, iş parçacığı güvenli olmayan sürümü daha yavaş ölçeklendirmek iş parçacığı türü neden olabilir.  
  
 Aşağıdaki bölümlerde, okuma etrafında bir kullanıcı tarafından sağlanan kilit sahip iş parçacığı güvenli olmayan karşılığını karşı bir iş parçacığı güvenli koleksiyonu kullanmanız ve yazma işlemlerinin ne zaman hakkında genel rehberlik sağlar. Performans çok sayıda etkene bağlı olarak farklılık gösterebileceğinden, rehberlik belirli değil ve her koşulda mutlaka geçerli değil. Performans çok önemli ise, hangi koleksiyon türünün kullanılacağını belirlemek için en iyi yolu temsil eden bilgisayar yapılandırmalarını ve yükleri göre performansını ölçmek için ise. Bu belge aşağıdaki terimler kullanılmaktadır:  
  
 *Saf üretici-tüketici senaryosu*  
 Verilen herhangi bir iş parçacığı ekleme veya öğeleri, ancak ikisini birden kaldırılıyor.  
  
 *Üretici-tüketici karışık senaryo*  
 Verilen herhangi bir iş parçacığı hem ekleme ve öğelerin kaldırılması.  
  
 *Hızlandırmayı*  
 Algoritmik performans aynı senaryosunda başka bir türüne göre daha hızlı.  
  
 *Ölçeklenebilirlik*  
 Çekirdek bilgisayarda orantılıdır performansın artış. İki çekirdek üzerinde gösterilenden ölçeklenen bir algoritma sekiz çekirdeği daha hızlı gerçekleştirir.  
  
## <a name="concurrentqueuet-vs-queuet"></a>ConcurrentQueue(T) vs. Queue(T)  
 Saf üretici-tüketici senaryolarında, işleme süresinin her öğe için olduğu çok küçük (bazı yönergeler), ardından <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> büyüklükteki performans avantajlarının üzerinden sunabilir bir <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> dış bir kilit sahip. Bu senaryoda, <xref:System.Collections.Concurrent.ConcurrentQueue%601> tek bir adanmış iş parçacığı queuing ve tek bir adanmış iş parçacığı kuyruktan çıkarılması olduğunda en iyi şekilde çalışır. Bu kural, ardından zorlama, <xref:System.Collections.Generic.Queue%601> bile gerçekleştirebileceği kıyasla biraz daha hızlı <xref:System.Collections.Concurrent.ConcurrentQueue%601> birden çok çekirdeğe sahip bilgisayarlarda.  
  
 Ne zaman işlem süresi yaklaşık 500 FLOPS (kayan nokta işlemleri) veya daha sonra iki iş parçacığı kuralı uygulanmaz <xref:System.Collections.Concurrent.ConcurrentQueue%601>, daha sonra çok iyi bir ölçeklendirilebilirliğe sahip. <xref:System.Collections.Generic.Queue%601> Bu senaryoda iyi ölçeklenmez.  
  
 İşlem süresi çok küçük olduğunda, üretici-tüketici senaryoları, karma bir <xref:System.Collections.Generic.Queue%601> dış olan kilit ölçeklenen daha iyi <xref:System.Collections.Concurrent.ConcurrentQueue%601> yapar. Ancak, işleme süresi olduğunda yaklaşık 500 FLOPS veya daha sonra <xref:System.Collections.Concurrent.ConcurrentQueue%601> daha iyi ölçeklenir.  
  
## <a name="concurrentstack-vs-stack"></a>ConcurrentStack vs. Yığın  
 Saf üretici-tüketici senaryolarında, işleme süresinin ardından çok küçük olduğunda <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType> ve <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> dış olan kilit hakkında bir adanmış gönderme iş parçacığı ve adanmış bir yığından kaldırılıyor iş parçacığı ile aynı büyük olasılıkla gerçekleştirir. Ancak, sayısı arttıkça iş parçacığı, iki türü de artan Çekişme nedeniyle yavaşlamasına ve <xref:System.Collections.Generic.Stack%601> gerçekleştirebileceğiniz daha iyi <xref:System.Collections.Concurrent.ConcurrentStack%601>. İşlem süresi yaklaşık 500 FLOPS olduğunda veya daha fazla ve ardından her iki tür ölçekli olarak aynı fiyat hakkında.  
  
 Üretici-tüketici senaryoları, karma olarak <xref:System.Collections.Concurrent.ConcurrentStack%601> küçük ve büyük iş yükleri için daha hızlıdır.  
  
 Kullanımını <xref:System.Collections.Concurrent.ConcurrentStack%601.PushRange%2A> ve <xref:System.Collections.Concurrent.ConcurrentStack%601.TryPopRange%2A> erişim sürelerini önemli ölçüde hızlandırmak.  
  
## <a name="concurrentdictionary-vs-dictionary"></a>ConcurrentDictionary vs. Sözlük  
 Genel olarak, bir <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> hiçbir senaryoda Burada, ekleme ve anahtarlar veya değerler aynı anda birden çok iş parçacığından güncelleştiriliyor. Sık güncelleştirmeler ve nispeten az okuma içeren senaryolarda <xref:System.Collections.Concurrent.ConcurrentDictionary%602> genellikle büyüklükteki avantaj sunar. Birçok okuma ve çok sayıda güncelleştirme içeren senaryolarda <xref:System.Collections.Concurrent.ConcurrentDictionary%602> genel olarak, herhangi bir sayıda çekirdek bilgisayarlarda önemli ölçüde daha hızlı gerçekleşir.  
  
 Sık güncelleştirmeler içeren senaryolarda eşzamanlılık derecesini artırabilirsiniz <xref:System.Collections.Concurrent.ConcurrentDictionary%602> ve performansı daha fazla çekirdeğe sahip bilgisayarlarda artırır olup olmadığını görmek için ardından ölçün. Eşzamanlılık düzeyi değiştirme, genel işlemlerini mümkün olduğunca kaçının.  
  
 Anahtar ya da değerler yalnızca okuma yapıyorsanız <xref:System.Collections.Generic.Dictionary%602> sözlük tüm iş parçacıklarının engellemelerinden değiştirilmeyen eşitleme gereklidir çünkü daha hızlıdır.  
  
## <a name="concurrentbag"></a>ConcurrentBag  
 Saf üretici-tüketici senaryolarda <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> büyük olasılıkla diğer eşzamanlı koleksiyon türleri daha yavaş gerçekleştirir.  
  
 Üretici-tüketici senaryoları, karma olarak <xref:System.Collections.Concurrent.ConcurrentBag%601> genellikle çok daha hızlı ve daha ölçeklenebilir daha küçük ve büyük ölçekli iş yükleri için başka bir eşzamanlı koleksiyon türü.  
  
## <a name="blockingcollection"></a>BlockingCollection  
 Sınırlama ve engelleme semantiği gerekli olduğunda <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> büyük olasılıkla herhangi bir özel uygulama daha hızlı gerçekleştirir. Ayrıca, zengin iptal, numaralandırma ve özel durum işleme de destekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [İş Parçacığı Güvenli Koleksiyonları](../../../../docs/standard/collections/thread-safe/index.md)  
- [Paralel Programlama](../../../../docs/standard/parallel-programming/index.md)
