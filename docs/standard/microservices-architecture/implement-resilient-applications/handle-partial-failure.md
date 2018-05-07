---
title: Kısmi hata işleme
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Kısmi hata işleme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 26e3d6b4cd1df051c00cef4ee8370ca9c213363e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="handling-partial-failure"></a>Kısmi hata işleme

Mikro tabanlı uygulamalar gibi dağıtılan sistemlerde, kısmi hatanın ever-present bir risk vardır. Örneği için tek bir mikro hizmet/kapsayıcısı başarısız olabilir veya kısa bir süre yanıtlamak kullanılamıyor olabilir veya tek bir VM veya sunucu çökebilir. Bir hizmet, istemciler ve hizmetler ayrı işlemler olduğundan, bir istemcinin isteğini zamanında bir şekilde yanıt verebilir olmayabilir. Hizmet isteklerini aşırı yüklenmiş ve için son derece yavaş yanıt veren olabilir veya yalnızca ağ sorunları nedeniyle kısa bir süre için erişilebilir olmayabilir.

Örneğin, eShopOnContainers sipariş ayrıntılarını sayfasından örnek uygulamayı göz önünde bulundurun. Sıralama mikro hizmet yanıt vermiyorsa kullanıcı bulunduğunda istemci işleminin (MVC web uygulaması) hatalı bir uygulama bir sipariş göndermek — Örneğin, zaman uyumlu RPC'ler hiçbir zaman aşımı ile kullanmak için istemci kodu olsaydı — iş parçacığı süresiz olarak engeller yanıt bekleme. Hatalı kullanıcı deneyimi oluşturma, ek olarak her yanıt bekleme kullanır veya bir iş parçacığı engeller ve iş parçacıkları yüksek düzeyde ölçeklenebilir uygulamalar çok değerli. Sonunda birçok engellenmiş iş parçacığı varsa, uygulamanın çalışma zamanı iş parçacığı dışında çalıştırabilirsiniz. Bu durumda, uygulamanın yerine genel yanıt veremez hale gelebilir Göster Şekil 10-1 olarak yalnızca kısmen yanıt.

![](./media/image1.png)

**Şekil 10-1**. Kısmi hatalar nedeniyle hizmet iş parçacığı kullanılabilirliği etkileyen bağımlılıkları

Özellikle iç mikro etkileşim çoğunu (hangi koruma düzeni olarak kabul edilir) zaman uyumlu HTTP çağrıları alıyorsa büyük mikro tabanlı bir uygulama, kısmi bir hatası, yükseltilmiş. Gün başına gelen çağrıları milyonlarca alan bir sistem düşünün. Bu gelen çağrıları sisteminizi uzun zaman uyumlu HTTP çağrıları zincirleri üzerinde temel hatalı bir tasarım varsa, daha fazla giden çağrıları (1:4 oranını şimdi varsayalım) milyonlarca iç mikro düzinelerce için zaman uyumlu bağımlılıklar olarak neden olabilir. Bu durum, Şekil 10-2'de, özellikle bağımlılık gösterilen \#3.

![](./media/image2.png)

**Şekil 10-2**. HTTP isteklerinin uzun zincirleri özelliklerine sahip bir yanlış tasarım olan etkisi

Aralıklı hatasıdır neredeyse dağıtılmış bir garanti ve her bağımlılık mükemmel kullanılabilirlik olsa bile tabanlı sistem, bulut. Bu, göz önünde bulundurmanız gereken bir olgu olması gerekir.

Bile küçük kapalı kalma süreleri, değil tasarlayıp teknikleri hataya dayanıklılık sağlamak için yükseltilmiş. Bir örnek olarak, bu ripple etkisi nedeniyle birkaç saat kalma süresi içinde her ay 50 bağımlılıklarla her % 99,99 kullanılabilirlik neden olur. Mikro hizmet bağımlılık istekleri yüksek hacimli işlerken başarısız olduğunda, bu hata hızla her hizmetindeki tüm kullanılabilir isteği iş parçacıklarını saturate ve tüm uygulama kilitlenme.

![](./media/image3.png)

**Şekil 10-3**. Zaman uyumlu HTTP çağrıları uzun zincirleri ile mikro tarafından yükseltilmiş kısmi hatası

Bölümünde bu sorunu en aza indirmek için "*zaman uyumsuz mikro hizmet tümleştirme zorunlu mikro'nın otonomisi*" (mimarisi bölümde), biz zaman uyumsuz iletişim iç kullanmanızı teşvik mikro. Biz kısaca daha sonraki bölümde açıklanmaktadır.

Buna ek olarak, kısmi hataları işlemek için mikro ve istemci uygulamaları tasarım temel — diğer bir deyişle, esnek mikro ve istemci uygulamaları oluşturmak için.


>[!div class="step-by-step"]
[Önceki] (index.md) [sonraki] (kısmi hatası strategies.md)
