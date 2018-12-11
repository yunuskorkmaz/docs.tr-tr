---
title: Kısmi hata işleme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Kısmi hata işleme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: 94239fc30292760b2bb28849f8c6ab72c7ceb33d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53144734"
---
# <a name="handling-partial-failure"></a>Kısmi hata işleme

Mikro hizmet tabanlı uygulamalar gibi dağıtılmış sistemlerde ardı arkası bir kısmi hata riskini yoktur. Örneği için tek bir mikro hizmet/kapsayıcı başarısız olabilir veya yanıtlamak için kısa bir süre kullanılamıyor olabilir veya tek bir VM veya sunucusuna çökebilir. İstemcileri ve Hizmetleri ayrı işlemler olduğundan, hizmet istemci isteğini zamanında bir şekilde yanıt vermesi mümkün olmayabilir. Hizmet aşırı yüklenmiş ve yanıt için son derece yavaş istekler olabilir veya yalnızca ağ sorunları nedeniyle kısa bir süre için erişilebilir olmayabilir.

Örneğin, Sipariş Ayrıntıları sayfasından hizmetine örnek uygulamayı düşünün. Sıralama mikro hizmet yanıt vermiyorsa, kullanıcı çalışır (MVC web uygulaması) istemci işleminin hatalı bir uygulama bir sipariş göndermek — Örneğin, zaman uyumlu RPC hiçbir zaman aşımı ile kullanmak için istemci kodu oluşturduysanız — iş parçacıkları süresiz olarak engeller Yanıt bekleniyor. Olumsuz kullanıcı deneyiminden oluşturma, ek olarak her yanıt bekleme kullanan veya bir iş parçacığını engeller ve iş parçacığı son derece yüksek oranda ölçeklenebilir uygulamalar değerlidir. Sonuçta pek çok engellenen iş parçacıkları varsa, uygulamanın çalışma zamanı iş parçacığı dışında çalıştırabilirsiniz. Bu durumda, uygulamanın genel yerine bırakabiliyor show Şekil 10-1 olarak yalnızca kısmen yanıt.

![](./media/image1.png)

**Şekil 10-1**. Hizmet iş parçacığı kullanılabilirliğini etkileyebilecek bağımlılıklar nedeniyle kısmi hataları

Özellikle çoğu iç mikro hizmetler etkileşimi (Bu bir önleyici deseni olarak kabul edilir) zaman uyumlu HTTP çağrıları alıyorsa bir büyük mikro hizmet tabanlı uygulama içinde kısmi herhangi bir hata, yükseltilmiş. Gelen çağrılar her gün milyonlarca alan bir sistem hakkında düşünün. Bu gelen çağrıları sisteminizi uzun zaman uyumlu HTTP çağrıları zincirleri üzerinde alan hatalı bir tasarım varsa, (1:4 oranını varsayalım) giden çağrıları çok daha fazla milyonlarca iç mikro hizmetler onlarca için zaman uyumlu bağımlılıkları olarak neden olabilir. Bu durum, Şekil 10-2'de, özellikle bağımlılık gösterilen \#3.

![](./media/image2.png)

**Şekil 10-2**. HTTP isteklerini uzun zincirleri özelliklerine sahip hatalı bir tasarım sahip olmanın etkisi

Her bağımlılık mükemmel kullanılabilirlik olsa bile, aralıklı olarak ortaya çıkan hata dağıtılmış ve bulut tabanlı bir sistemde garanti edilir. Bunu göz önünde bulundurmanız gereken gerçeğidir.

Daha küçük bir kapalı kalma süreleri, değil tasarlayıp teknikleri hataya dayanıklılık sağlamak için yükseltilmiş. Örneğin, 50 bağımlılıkları her olan % 99,99 oranında kullanılabilirlik birkaç saat kapalı kalma süresi içinde her ay nedeniyle bu dalgalanma etkisine neden olur. Yüksek hacimli istekleriniz işlerken bir mikro hizmet bağımlılık başarısız olduğunda, bu hata hızlı bir şekilde her hizmetin tüm kullanılabilir istek iş parçacıklarının saturate ve tüm uygulama kilitlenme.

![](./media/image3.png)

**Şekil 10-3**. Kısmi hata uzun zincirleri zaman uyumlu HTTP çağrıları ile mikro hizmetler tarafından yükseltilmiş

Bölümünde, bu sorunu en aza indirmek için "*zaman uyumsuz bir mikro hizmet tümleştirmesi zorunlu mikro hizmet'ın bağımsız çalışma sınırı*" (mimarisi bölümde ise), bu kılavuzun arasında zaman uyumsuz iletişim kullanmanızı önerir İç mikro hizmetler. 

Ayrıca, temel kısmi hatalarını işlemek için mikro Hizmetleri ve istemci uygulamalarınızı tasarlama — diğer bir deyişle, esnek bir mikro hizmet ve istemci uygulamaları oluşturmak için.

>[!div class="step-by-step"]
>[Önceki](index.md)
>[İleri](partial-failure-strategies.md)