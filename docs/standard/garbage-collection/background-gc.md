---
title: Arka plan çöp toplama
description: .NET'te arka plan çöp toplama ve iş istasyonu ve sunucu çöp toplama da nasıl farklılık olduğu hakkında bilgi edinin.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: dcb1d348e679e07646273b8fbc4ea29b44ee4974
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82103564"
---
# <a name="background-garbage-collection"></a>Arka plan çöp toplama

Arka plançöp toplamada (GC), geçici nesiller (0 ve 1) gerektiğinde toplanırve nesil 2'nin koleksiyonu devam eder. Arka plan çöp toplama, arka plan veya sunucu GC'sine bağlı olarak bir veya daha fazla özel iş parçacığı üzerinde gerçekleştirilir ve yalnızca nesil 2 koleksiyonları için geçerlidir.

Arka plan çöp toplama varsayılan olarak etkinleştirilir. .NET Framework uygulamalarındaki [gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) yapılandırma ayarı veya .NET Core uygulamalarındaki [System.GC.Eşzamanlı](../../core/run-time-config/garbage-collector.md#systemgcconcurrentcomplus_gcconcurrent) ayarı ile etkinleştirilebilir veya devre dışı tutulabilir.

> [!NOTE]
> Arka plan çöp [toplama eşzamanlı çöp toplama](#concurrent-garbage-collection) nın yerini alır ve .NET Framework 4 ve sonraki sürümlerde kullanılabilir. .NET Framework 4'te yalnızca iş *istasyonu* çöp toplama için desteklenir. .NET Framework 4.5 ile başlayarak, arka plan çöp toplama hem *iş istasyonu* hem de *sunucu* çöp toplama için kullanılabilir.

Arka plan çöp toplama sırasında geçici nesiller üzerine bir koleksiyon *ön planda* çöp toplama olarak bilinir. Ön plan çöp koleksiyonları oluştuğunda, yönetilen tüm iş parçacıkları askıya alınır.

Arka plan çöp toplama devam ediyor ve nesil 0'da yeterli nesne ayırdıysanız, CLR bir nesil 0 veya nesil 1 ön plan çöp toplama gerçekleştirir. Özel arka plan çöp toplama iş parçacığı, ön plan çöp toplama için bir istek olup olmadığını belirlemek için sık sık güvenli noktalarda denetler. Varsa, ön plan çöp toplama oluşabilir, böylece arka plan koleksiyonu kendini askıya alır. Ön plan çöp toplama tamamlandıktan sonra, özel arka plan çöp toplama iş parçacıkları ve kullanıcı iş parçacıkları devam eder.

Arka plan çöp toplama, arka plan çöp toplama sırasında geçici çöp koleksiyonları oluşabilir, çünkü eşzamanlı çöp toplama tarafından uygulanan ayırma kısıtlamaları kaldırır. Arka plan çöp toplama geçici nesillerde ölü nesneleri kaldırabilirsiniz. Ayrıca bir nesil 1 çöp toplama sırasında gerekirse yığın genişletebilirsiniz.

## <a name="background-workstation-vs-server-gc"></a>Arka plan iş istasyonu vs sunucu GC

.NET Framework 4.5 ile başlayarak, arka plan çöp toplama sunucu GC için kullanılabilir. Arka plan GC sunucu çöp toplama için varsayılan modudur.

Arka plan sunucusu çöp toplama işlevleri arka plan iş istasyonu çöp toplama benzer, ancak birkaç fark vardır:

- Arka plan iş istasyonu çöp toplama, arka plan sunucusu çöp toplama birden çok iş parçacığı kullanır ise bir özel arka plan çöp toplama iş parçacığı kullanır. Genellikle, her mantıksal işlemci için özel bir iş parçacığı vardır.

- İş istasyonu arka plan çöp toplama iş parçacığı aksine, arka plan sunucusu GC iş parçacıkları zaman dışarı yok.

Aşağıdaki resimde, ayrı, özel bir iş parçacığı üzerinde gerçekleştirilen arka plan *iş istasyonu* çöp toplama gösterilmektedir:

![Arka plan iş istasyonu çöp toplama](./media/fundamentals/background-workstation-garbage-collection.png)

Aşağıdaki resimde, ayrı, özel iş parçacıkları üzerinde gerçekleştirilen arka plan *sunucusu* çöp toplama gösterilmektedir:

![Arka plan sunucusu çöp toplama](./media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Eşzamanlı çöp toplama

> [!TIP]
> Bu bölüm aşağıdakiler için geçerlidir:
>
> - .NET Framework 3.5 ve daha önceki iş istasyonu çöp toplama
> - .NET Framework 4 ve daha önceki sunucu çöp toplama
>
> Eşzamanlı çöp sonraki sürümlerde arka plan çöp toplama ile değiştirilir.

İş istasyonu veya sunucu çöp toplama, iş parçacıkları toplama süresinin çoğu için çöp toplama gerçekleştiren özel bir iş parçacığı ile aynı anda çalışmasını sağlayan [eşzamanlı çöp toplama etkinleştirebilirsiniz.](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) Bu seçenek yalnızca nesil 2'deki çöp toplamaları etkiler; 0 ve 1.

Eşzamanlı çöp toplama, bir koleksiyon için duraklamaları en aza indirerek etkileşimli uygulamaların daha duyarlı olmasını sağlar. Yönetilen iş parçacıkları, eşzamanlı çöp toplama iş parçacığı çalışırken çoğu zaman çalışmaya devam edebilir. Bu, çöp toplama oluşurken daha kısa duraklamalara neden olur.

Eşzamanlı çöp toplama özel bir iş parçacığı üzerinde gerçekleştirilir. Varsayılan olarak, CLR hem tek işlemcili hem de çok işlemcili bilgisayarlarda eşzamanlı çöp toplama etkiniş istasyonu çöp toplama çalışır.

Aşağıdaki resimde, ayrı bir özel iş parçacığı üzerinde gerçekleştirilen eşzamanlı çöp toplama gösterilmektedir.

![Eşzamanlı Çöp Toplama İşparçacıkları](./media/gc-concurrent.png)

## <a name="see-also"></a>Ayrıca bkz.

- [İş istasyonu ve sunucu çöp toplama](workstation-server-gc.md)
- [Çöp toplama için çalışma zamanı yapılandırma seçenekleri](../../core/run-time-config/garbage-collector.md)
