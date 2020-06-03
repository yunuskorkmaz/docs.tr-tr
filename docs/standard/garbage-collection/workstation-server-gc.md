---
title: İş istasyonu ve sunucu atık toplama (GC)
description: .NET ' te iş istasyonu ve sunucu atık toplama hakkında bilgi edinin.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 5ff2b1fe2f997913e071f35ec5abb167ed757608
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84306701"
---
# <a name="workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu atık toplama

Çöp toplayıcı kendi kendini ayarlamadır ve çok çeşitli senaryolarda çalışabilir. Ancak, [çöp toplamanın türünü](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) iş yükünün özelliklerine göre ayarlayabilirsiniz. CLR aşağıdaki çöp toplama türlerini sağlar:

- İstemci uygulamaları için tasarlanan iş istasyonu atık toplama (GC). Tek başına uygulamalar için varsayılan GC Flavor ' dir. Barındırılan uygulamalarda, örneğin, ASP.NET tarafından barındırılan uygulamalar için, ana bilgisayar varsayılan GC özelliğini belirler.

  İş istasyonu atık toplama işlemi eşzamanlı olabilir veya eşzamanlı olmayan bir şekilde olabilir. Eş zamanlı (veya *arka plan*) çöp toplama, yönetilen iş parçacıklarının çöp toplama sırasında işlemlere devam etmesine olanak sağlar. [Arka plan atık toplama](background-gc.md) , .NET Framework 4 ve sonraki sürümlerde [eşzamanlı çöp toplama](background-gc.md#concurrent-garbage-collection) yerini alır.

- Yüksek aktarım hızı ve ölçeklenebilirlik gerektiren sunucu uygulamalarına yönelik olan sunucu çöp toplama.

  - .NET Core 'da, sunucu çöp toplama, eş zamanlı olmayan veya arka plan olabilir.

  - .NET Framework 4,5 ve sonraki sürümlerinde, sunucu çöp toplama, eş zamanlı olmayan veya arka plan olabilir. .NET Framework 4 ve önceki sürümlerde, sunucu çöp toplama işlemi eşzamanlı değildir.

Aşağıdaki çizimde, bir sunucusunda çöp toplamayı gerçekleştiren adanmış iş parçacıkları gösterilmektedir:

![Sunucu atık toplama Iş parçacıkları](media/gc-server.png)

## <a name="performance-considerations"></a>Performansla ilgili önemli noktalar

### <a name="workstation-gc"></a>İş istasyonu GC

İş istasyonu çöp toplama işlemi için iş parçacığı ve performans değerlendirmeleri aşağıda verilmiştir:

- Koleksiyon, çöp toplamayı tetikleyen ve aynı önceliğe kalan Kullanıcı iş parçacığında oluşur. Kullanıcı iş parçacıkları genellikle normal öncelikte çalıştığı için çöp toplayıcı (normal bir öncelikli iş parçacığı üzerinde çalışır), CPU süresi için diğer iş parçacıklarıyla rekabet etmelidir. (Yerel kod çalıştıran iş parçacıkları sunucu veya iş istasyonu çöp toplamadan askıya alınmaz.)

- İş istasyonu çöp toplama her zaman, [yapılandırma ayarından](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)bağımsız olarak yalnızca bir işlemciye sahip olan bir bilgisayarda kullanılır.

### <a name="server-gc"></a>Sunucu GC

Aşağıda sunucu çöp toplama için iş parçacığı ve performans konuları verilmiştir:

- Koleksiyon, öncelik düzeyinde çalışan birden fazla adanmış iş parçacığında oluşur `THREAD_PRIORITY_HIGHEST` .

- Her CPU için bir yığın ve bir ayrılmış iş parçacığı her CPU için sağlanır ve sayfa@@ 'ler aynı anda toplanır. Her yığın küçük bir nesne yığını ve büyük bir nesne yığını içerir ve tüm yığınlara Kullanıcı kodu tarafından erişilebilir. Farklı yığınlardaki nesneler birbirlerine başvurabilir.

- Birden çok çöp toplama iş parçacığı birlikte çalıştığından, sunucu çöp toplama, aynı boyuttaki yığında iş istasyonu atık toplamadan daha hızlıdır.

- Sunucu çöp toplama genellikle daha büyük boyut segmentlerine sahiptir. Ancak, bu yalnızca bir Genelleştirme 'dir: kesim boyutu uygulamaya özeldir ve değiştirilebilir. Uygulamanızı ayarlamaya yönelik çöp toplayıcı tarafından ayrılan parçaların boyutu hakkında varsayımlar yapmayın.

- Sunucu atık toplama, kaynak kullanımı yoğun olabilir. Örneğin, dört işlemcili bir bilgisayarda çalışan sunucu GC 'yi kullanan 12 işlem olduğunu düşünün. Tüm süreçler aynı anda çöp toplama işlemi gerçekleşiyorsa, aynı işlemcide zamanlanan 12 iş parçacığı olduğu için birbirleriyle karışacaktır. Süreçler etkinse, hepsi sunucu GC 'yi kullanmak iyi bir fikir değildir.

Bir uygulamanın yüzlerce örneğini çalıştırıyorsanız, eşzamanlı atık toplama devre dışı bırakılmış iş istasyonu çöp toplamayı kullanmayı düşünün. Bu, performansı iyileştirebilen daha az bağlam geçişe neden olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Arka plan atık toplama](background-gc.md)
- [Çöp toplama için çalışma zamanı yapılandırma seçenekleri](../../core/run-time-config/garbage-collector.md)
