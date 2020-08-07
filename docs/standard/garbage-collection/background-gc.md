---
title: Arka plan atık toplama
description: .NET ' te arka plan atık toplama ve iş istasyonu ve sunucu çöp toplama bölümünde farklılık gösteren bilgi edinin.
ms.date: 04/21/2020
helpviewer_keywords:
- garbage collection, background
- background garbage collection
ms.openlocfilehash: bf88c14b2aeed94a548b6116749fa8669576afe1
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916997"
---
# <a name="background-garbage-collection"></a>Arka plan atık toplama

Arka plan atık toplama (GC) içinde, 2. nesil toplama işlemi devam ederken, kısa ömürlü nesiller (0 ve 1) gerektiği şekilde toplanır. Arka plan atık toplama, arka plan veya sunucu GC olmasına bağlı olarak bir veya daha fazla adanmış iş parçacığında gerçekleştirilir ve yalnızca 2. nesil koleksiyonlar için geçerlidir.

Arka plan atık toplama varsayılan olarak etkindir. .NET Framework uygulamalarında [gcConcurrent](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) yapılandırma ayarıyla etkinleştirilebilir veya devre dışı bırakılabilir, .NET Core ve .NET 5 ve sonraki uygulamalardaki [System. GC. eşzamanlı](../../core/run-time-config/garbage-collector.md#background-gc) ayarı.

> [!NOTE]
> Arka plan atık toplama, [eşzamanlı atık toplamayı](#concurrent-garbage-collection) değiştirir ve .NET Framework 4 ve sonraki sürümlerde kullanılabilir. .NET Framework 4 ' te yalnızca *iş istasyonu* çöp toplama için desteklenir. .NET Framework 4,5 ' den başlayarak, arka plan atık toplama, hem *iş istasyonu* hem de *sunucu* çöp toplama için kullanılabilir.

Arka plan atık toplama sırasında kısa ömürlü oluşumlara yönelik bir koleksiyon, *ön plan* atık toplama olarak bilinir. Ön plan atık koleksiyonları gerçekleştiğinde, tüm yönetilen iş parçacıkları askıya alınır.

Arka plan atık toplama işlemi devam ederken ve nesil 0 ' da yeterli nesne ayırdığınızda CLR, 1. nesil bir ön plan atık toplama işlemi gerçekleştirir. Adanmış arka plan atık toplama iş parçacığı, ön plan atık toplama için bir istek olup olmadığını anlamak için sık kullanılan güvenli noktaları denetler. Varsa, ön plan atık toplama işleminin gerçekleşmesi için arka plan koleksiyonu kendisini askıya alır. Ön plan atık toplama işlemi tamamlandıktan sonra, adanmış arka plan atık toplama iş parçacıkları ve Kullanıcı iş parçacıkları sürdürülür.

Arka plan atık toplama sırasında kısa ömürlü çöp koleksiyonları gerçekleşebildiğinden arka plan atık toplama, eşzamanlı atık toplama tarafından uygulanan ayırma kısıtlamalarını ortadan kaldırır. Arka plan atık toplama, kısa ömürlü neslerdeki ölü nesneleri kaldırabilir. Ayrıca, 1. nesil atık toplama işlemi sırasında gerekirse yığını genişletebilir.

## <a name="background-workstation-vs-server-gc"></a>Arka plan iş istasyonu ile sunucu GC

.NET Framework 4,5 ' den başlayarak, arka plan atık toplama, Server GC için kullanılabilir. Arka plan GC, sunucu çöp toplama için varsayılan moddur.

Arka plan sunucusu çöp toplama, arka plan iş istasyonu çöp toplamaya benzer şekilde çalışır, ancak bazı farklılıklar vardır:

- Arka plan iş istasyonu çöp toplama, bir adanmış arka plan atık toplama iş parçacığı kullanır, ancak arka plan sunucusu çöp toplama birden çok iş Genellikle, her mantıksal işlemci için adanmış bir iş parçacığı vardır.

- İş istasyonu arka plan atık toplama iş parçacığından farklı olarak, arka plan sunucusu GC iş parçacıkları zaman aşımına uğrar.

Aşağıdaki çizimde, ayrı ve adanmış bir iş parçacığında gerçekleştirilen arka plan *iş istasyonu* çöp toplama işlemi gösterilmektedir:

![Arka plan iş istasyonu çöp toplama](media/fundamentals/background-workstation-garbage-collection.png)

Aşağıdaki çizimde, ayrı ve adanmış iş parçacıklarında gerçekleştirilen arka plan *sunucusu* çöp toplama işlemi gösterilmektedir:

![Arka plan sunucusu çöp toplama](media/fundamentals/background-server-garbage-collection.png)

## <a name="concurrent-garbage-collection"></a>Eşzamanlı atık toplama

> [!TIP]
> Bu bölüm için geçerlidir:
>
> - İş istasyonu atık toplama için .NET Framework 3,5 ve öncesi
> - Sunucu atık toplama için .NET Framework 4 ve öncesi
>
> Eş zamanlı atık, sonraki sürümlerde arka plan atık toplama ile değiştirilmiştir.

İş istasyonu veya sunucu çöp toplama bölümünde, iş parçacıklarının, koleksiyon süresince büyük bir süre için çöp toplamayı gerçekleştiren adanmış bir iş parçacığıyla eşzamanlı olarak çalışmasını sağlayan [eşzamanlı atık toplamayı etkinleştirebilirsiniz](../../framework/configure-apps/file-schema/runtime/gcconcurrent-element.md). Bu seçenek, kuşak 2 ' de yalnızca çöp koleksiyonlarını etkiler; nesil 0 ve 1 her zaman eşzamanlı değildir çünkü hızlı bir şekilde tamamlanır.

Eşzamanlı atık toplama, bir koleksiyon için duraklamaları en aza indirerek etkileşimli uygulamaların daha fazla yanıt vermesini sağlar. Yönetilen iş parçacıkları, eşzamanlı atık toplama iş parçacığı çalışırken çoğu zaman çalışmaya devam edebilir. Bu tasarım, bir çöp toplama işlemi sırasında daha kısa duraklamalar elde edilir.

Eş zamanlı çöp toplama, adanmış bir iş parçacığında gerçekleştirilir. Varsayılan olarak, CLR hem tek işlemci hem de çok işlemcili bilgisayarlarda eşzamanlı çöp toplama özellikli iş istasyonu çöp toplamayı çalıştırır.

Aşağıdaki çizimde ayrı bir adanmış iş parçacığında gerçekleştirilen eşzamanlı çöp toplama gösterilmektedir.

![Eşzamanlı atık toplama Iş parçacıkları](media/gc-concurrent.png)

## <a name="see-also"></a>Ayrıca bkz.

- [İş istasyonu ve sunucu atık toplama](workstation-server-gc.md)
- [Çöp toplama için çalışma zamanı yapılandırma seçenekleri](../../core/run-time-config/garbage-collector.md)
