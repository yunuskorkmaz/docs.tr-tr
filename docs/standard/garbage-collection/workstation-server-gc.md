---
title: İş istasyonu ve sunucu çöp toplama (GC)
description: .NET'te iş istasyonu ve sunucu çöp toplama hakkında bilgi edinin.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, workstation
- garbage collection, server
- workstation garbage collection
- server garbage collection
ms.openlocfilehash: 6b8e5f6802e5d44669b95d43d4e897fa4a418512
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103557"
---
# <a name="workstation-and-server-garbage-collection"></a>İş istasyonu ve sunucu çöp toplama

Çöp toplayıcı kendi kendini ayarlıyor ve çok çeşitli senaryolarda çalışabilir. Ancak, [iş yükünün](../../core/run-time-config/garbage-collector.md#flavors-of-garbage-collection) özelliklerine göre çöp toplama türünü ayarlayabilirsiniz. CLR aşağıdaki çöp toplama türlerini sağlar:

- İstemci uygulamaları için tasarlanmış iş istasyonu çöp toplama (GC). Bağımsız uygulamalar için varsayılan GC tadıdır. Barındırılan uygulamalar için, örneğin, ASP.NET tarafından barındırılan uygulamalar için, ana bilgisayar varsayılan GC lezzetini belirler.

  İş istasyonu çöp toplama eşzamanlı veya eşzamanlı olmayan olabilir. Eşzamanlı (veya *arka plan)* çöp toplama, yönetilen iş parçacıklarının çöp toplama sırasında işlemlerine devam etmesini sağlar. [Arka plan çöp toplama](background-gc.md) ,NET Framework 4 ve sonraki sürümlerde [eşzamanlı çöp toplama](background-gc.md#concurrent-garbage-collection) değiştirir.

- Yüksek iş gücü ve ölçeklenebilirlik gerektiren sunucu uygulamaları için tasarlanmış sunucu çöp toplama.

  - .NET Core'da sunucu çöp toplama eşzamanlı olmayan veya arka plan olabilir.

  - .NET Framework 4.5 ve sonraki sürümlerde sunucu çöp toplama eşzamanlı olmayan veya arka plan olabilir. .NET Framework 4 ve önceki sürümlerde sunucu çöp toplama eşzamanlı değildir.

Aşağıdaki resimde, bir sunucuda çöp toplama işlemini gerçekleştiren özel iş parçacıkları gösterilmektedir:

![Sunucu Çöp Toplama İş parçacıkları](./media/gc-server.png)

## <a name="performance-considerations"></a>Performansla ilgili önemli noktalar

### <a name="workstation-gc"></a>İş istasyonu GC

İş istasyonu çöp toplama için iş parçacığı ve performans hususları şunlardır:

- Koleksiyon, çöp toplamayı tetikleyen kullanıcı iş parçacığında oluşur ve aynı öncelikte kalır. Kullanıcı iş parçacıkları genellikle normal öncelikte çalıştığından, çöp toplayıcı (normal bir öncelik iş parçacığı üzerinde çalışır) CPU süresi için diğer iş parçacıkları ile rekabet etmelidir. (Yerel kodu çalıştıran iş parçacıkları sunucu veya iş istasyonu çöp toplama da askıya alınmaz.)

- İş istasyonu çöp toplama, [yapılandırma ayarından](../../core/run-time-config/garbage-collector.md#systemgcservercomplus_gcserver)bağımsız olarak her zaman yalnızca bir işlemciye sahip bir bilgisayarda kullanılır.

### <a name="server-gc"></a>Sunucu GC

Sunucu çöp toplama için iş parçacığı ve performans konuları şunlardır:

- Koleksiyon, `THREAD_PRIORITY_HIGHEST` öncelik düzeyinde çalışan birden çok özel iş parçacığı üzerinde oluşur.

- Her CPU için çöp toplama yapmak için bir yığın ve özel bir iş parçacığı sağlanır ve yığınlar aynı anda toplanır. Her yığın küçük bir nesne yığını ve büyük bir nesne yığını içerir ve tüm yığınlara kullanıcı koduyla erişilebilir. Farklı yığınlar üzerindeki nesneler birbirine başvurabilir.

- Birden çok çöp toplama iş parçacığı birlikte çalıştığıiçin, sunucu çöp toplama aynı boyuttaki yığındaki iş istasyonu çöp toplama işleminden daha hızlıdır.

- Sunucu çöp toplama genellikle daha büyük boyutlu segmentleri vardır. Ancak, bu yalnızca bir genellemedir: segment boyutu uygulamaya özgüdür ve değiştirilebilir. Uygulamanızı alarken çöp toplayıcıtarafından ayrılan segmentlerin boyutu hakkında varsayımlarda bulunmayın.

- Sunucu çöp toplama kaynak yoğun olabilir. Örneğin, dört işlemcisi olan bir bilgisayarda çalışan sunucu GC kullanan 12 işlem olduğunu düşünün. Tüm işlemler aynı anda çöp toplamak için olur, onlar birbirlerine müdahale olur, aynı işlemci üzerinde zamanlanmış 12 iş parçacığı olurdu. İşlemler etkinse, hepsinin sunucu GC'sini kullanmasını sağlamak iyi bir fikir değildir.

Bir uygulamanın yüzlerce örneğini çalıştırıyorsanız, eşzamanlı çöp toplama devre dışı bırakılmış iş istasyonu çöp toplama kullanmayı düşünün. Bu, performansı artırabilecek daha az bağlam geçişine neden olur.

## <a name="see-also"></a>Ayrıca bkz.

- [Arka plan çöp toplama](background-gc.md)
- [Çöp toplama için çalışma zamanı yapılandırma seçenekleri](../../core/run-time-config/garbage-collector.md)
